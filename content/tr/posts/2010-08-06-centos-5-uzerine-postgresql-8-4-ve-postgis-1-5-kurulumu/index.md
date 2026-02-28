---
title: "CentOS 5 üzerine PostgreSQL 8.4 ve PostGIS 1.5 kurulumu"
slug: "centos-5-uzerine-postgresql-8-4-ve-postgis-1-5-kurulumu"
date: 2010-08-06
---

![](images/stock_elephant_060.gif "PostGIS")Bu yazıda adım adım temiz CentOS 5 (64bit) sunucu üzerine PostgreSQL ve PostGIS 1.5 kurulumunun nasıl yapılacağını anlatacağım.

**1) PostgreSQL 8.4.2 kurulumu**

Öncelikle Devrim Gündüz tarafından hazırlanan [PostgreSQL YUM havuzunu](http://yum.pgrpms.org) kendi YUM havuz listemize eklememiz gerekiyor. Daha sonra postgresql-server ve postgresql-devel paketlerini kurmanız gerekiyor.

```
rpm -ihv http://yum.pgrpms.org/reporpms/8.4/pgdg-centos-8.4-2.noarch.rpm
#hangi postgresql paketlerinin var olduğuna bakalım
yum list | grep postgresql
#PostGIS derlenebilmesi icin postgresql-server paketi yanında
#postgresql-devel paketini de kurmamız gerekiyor
yum install postgresql-devel
yum install postgresql-server
service postgresql initdb
service postgresql start

```

PostgreSQL kurulumu bitti. PostgreSQL için pgAdmin III yazılımını kullanmanızı öneririm. Bunun için PostgreSQL'de uzak bağlantı için bazı ayarlar yapmanız gerekiyor. Bu adreste bulabilirsiniz: [http://www.cyberciti.biz/tips/postgres-allow-remote-access-tcp-connection.html](http://www.cyberciti.biz/tips/postgres-allow-remote-access-tcp-connection.html)

```
İpucu:
pg_hba.conf için yapacağınız düzenlemede,
host all all 0.0.0.0/0 trust
satırını eklerseniz tüm IP adresleri için uzak bağlantıya
izin vermiş olursunuz.

```

**2) PostGIS 1.5.1 kurulumu** <!--more--> PostGIS kurulumunu başarıyla yapabilmek için önce geometrik verilerin tutulması, sorgulanması, dönüşümü ve analizi için bazı paketlerin sistemde kurulu olması gerekiyor. Bu paketler; Proj ve GEOS.

Proj ve GEOS kurulumlarını kaynak koddan derleyerek gerçekleştireceğiz. Bu yüzden öncelikle sistemimizde gcc++ derleyici kurulumu yapıyoruz.

```
#eğer kurulu olduğundan eminseniz bu adımı atlayabilirsiniz.
yum install gcc-c++

```

Proj, GEOS ve PostGIS derlemelerini yapabilmek için geçici bir klasör oluşturalım.

```
mkdir /gisrc
cd /gisrc

```

[Proj](http://trac.osgeo.org/proj/) kurulumu:

```
cd /gisrc
mkdir proj
cd proj
wget http://download.osgeo.org/proj/proj-4.7.0.tar.gz
tar -xvf proj-4.7.0.tar.gz
wget http://download.osgeo.org/proj/proj-datumgrid-1.5.zip
unzip proj-datumgrid-1.5.zip  -d  proj-4.7.0/nad
cd proj-4.7.0
./configure
make
make install
ldconfig

```

[GEOS](http://trac.osgeo.org/geos/) kurulumu:

```
cd /gisrc
mkdir geos
cd geos
wget http://download.osgeo.org/geos/geos-3.2.2.tar.bz2
tar -xvf geos-3.2.2.tar.bz2
cd geos-3.2.2
./configure
make
make install
ldconfig

```

[libxml](http://www.xmlsoft.org/) kurulumu (bu kurulum PostGIS 1.5 ile gelen yeni bazı özellikleri kullanabilmeniz için gerekiyor):

```
cd /gisrc
mkdir libxml
cd libxml
wget ftp://xmlsoft.org/libxml2/libxml2-2.7.7.tar.gz
tar -xvf libxml2-2.7.7.tar.gz
cd libxml2-2.7.7
./configure
make
make install
ldconfig

```

Ve sıra geldi [PostGIS](http://postgis.refractions.net/) kurulumuna:

```
cd /gisrc
mkdir postgis
cd postgis
wget http://postgis.refractions.net/download/postgis-1.5.1.tar.gz
tar -xvf postgis-1.5.1.tar.gz
cd postgis-1.5.1
./configure
make
make install
ldconfig

```

Kurulum tamamlandıktan sonra 64bit mimariden kaynaklanan bazı değişiklikleri yapmamız gerekiyor.

```
#postgis bağımlılıklarını kontrol edelim
ldd -d /usr/lib64/pgsql/postgis-1.5.so
#çıktıda iki satır aşağıdaki gibi olmayacaktır ama biz olmasını istiyoruz.
#libgeos_c.so.1 => /usr/lib64/libgeos_c.so.1
#libproj.so.0 => /usr/lib64/libproj.so.0
#ama bu iki komutla bu sorunu çözeceğiz
ln -s /usr/local/lib/libgeos_c.so.1.6.2 /usr/lib64/libgeos_c.so.1
ln -s /usr/local/lib/libproj.so /usr/lib64/libproj.so.0

```

Artık PostGIS ile mekansal veritabanımızı oluşturabiliriz.

```
chown postgres:postgres /gisrc
su - postgres
cd /gisrc/postgis/postgis-1.5.1
createdb template_postgis15
createlang plpgsql template_postgis15
psql -d template_postgis15 -f postgis/postgis.sql
psql -d template_postgis15 -f spatial_ref_sys.sql
psql -d template_postgis15 -f doc/postgis_comments.sql

```

Hepsi bu kadar!
