![MIKES DATA WORK GIT REPO](https://raw.githubusercontent.com/mikesdatawork/images/master/git_mikes_data_work_banner_01.png "Mikes Data Work")        

# Check For AlwaysOn Primary Status With SQL
**Post Date: October 30, 2014**        



## Contents    
- [About Process](##About-Process)  
- [SQL Logic](#SQL-Logic)  
- [Build Info](#Build-Info)  
- [Author](#Author)  
- [License](#License)       

## About-Process

<p>This SQL logic will check to see if the instance you are running it on is the Primary in an AlwaysOn configuration.</p>     


## SQL-Logic
```SQL
declare @server_name varchar(255)
declare @availability_group_name varchar(255)
declare @check_if_primary varchar(255)
set @server_name = ( select cast(serverproperty('servername') as varchar(200)) )
set @availability_group_name = ( select name from sys.availability_groups )
set @check_if_primary = ( select sdhars.role_desc from sys.dm_hadr_availability_replica_states sdhars inner join sys.availability_groups sag on sdhars.group_id = sag.group_id where sag.name = @availability_group_name and sdhars.is_local = 1 )
 
if @check_if_primary = 'PRIMARY'
 begin
 print 'This Server: ' + @server_name + ' (IS) the PRIMARY'
 end
 else
 print 'This Server: ' + @server_name + ' (IS NOT) the PRIMARY'

```

[![WorksEveryTime](https://forthebadge.com/images/badges/60-percent-of-the-time-works-every-time.svg)](https://shitday.de/)

## Build-Info

| Build Quality | Build History |
|--|--|
|<table><tr><td>[![Build-Status](https://ci.appveyor.com/api/projects/status/pjxh5g91jpbh7t84?svg?style=flat-square)](#)</td></tr><tr><td>[![Coverage](https://coveralls.io/repos/github/tygerbytes/ResourceFitness/badge.svg?style=flat-square)](#)</td></tr><tr><td>[![Nuget](https://img.shields.io/nuget/v/TW.Resfit.Core.svg?style=flat-square)](#)</td></tr></table>|<table><tr><td>[![Build history](https://buildstats.info/appveyor/chart/tygerbytes/resourcefitness)](#)</td></tr></table>|

## Author

[![Gist](https://img.shields.io/badge/Gist-MikesDataWork-<COLOR>.svg)](https://gist.github.com/mikesdatawork)
[![Twitter](https://img.shields.io/badge/Twitter-MikesDataWork-<COLOR>.svg)](https://twitter.com/mikesdatawork)
[![Wordpress](https://img.shields.io/badge/Wordpress-MikesDataWork-<COLOR>.svg)](https://mikesdatawork.wordpress.com/)

    
## License
[![LicenseCCSA](https://img.shields.io/badge/License-CreativeCommonsSA-<COLOR>.svg)](https://creativecommons.org/share-your-work/licensing-types-examples/)

![Mikes Data Work](https://raw.githubusercontent.com/mikesdatawork/images/master/git_mikes_data_work_banner_02.png "Mikes Data Work")

