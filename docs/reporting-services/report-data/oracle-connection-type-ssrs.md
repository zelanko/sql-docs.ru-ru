---
title: Тип соединения Oracle (SSRS и сервер отчетов Power BI)
description: В этой статье о типе соединения Oracle вы узнаете, как создать источник данных.
ms.date: 03/12/2020
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: report-data
ms.topic: conceptual
ms.assetid: 9db86dd2-beda-42d8-8af7-2629d58a8e3d
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 425f864e31f1280fd31852de44a40d5e2d5c61ef
ms.sourcegitcommit: 783b35f6478006d654491cb52f6edf108acf2482
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/09/2020
ms.locfileid: "91891724"
---
# <a name="oracle-connection-type-ssrs--power-bi-report-server"></a>Тип соединения Oracle (SSRS и сервер отчетов Power BI)

Чтобы использовать в отчете данные из базы данных Oracle, необходим набор данных, основанный на источнике данных Oracle. Этот встроенный тип источника данных напрямую использует поставщик .NET Framework для Oracle и требует наличия клиентского программного обеспечения Oracle. В этой статье объясняется, как скачать и установить драйверы для Reporting Services, Сервера отчетов Power BI, построителя отчетов и Power BI Desktop.


Используйте сведения в этой статье для создания источника данных. Пошаговые инструкции см. в разделе [Добавление и проверка подключения к данным (построитель отчетов и службы SSRS)](../../reporting-services/report-data/add-and-verify-a-data-connection-report-builder-and-ssrs.md). 


## <a name="64-bit-drivers-for-the-report-servers"></a>64-разрядные драйверы для серверов отчетов

Сервер отчетов Power BI и SQL Server Reporting Services 2016 и более поздней версии используют **управляемый ODP.NET** для отчетов с разбивкой на страницы. Следующие шаги необходимы только при использовании драйверов Oracle ODAC 12.2 и более поздних версий, так как они по умолчанию устанавливаются в конфигурацию не на уровне компьютера для новой установки Oracle Home. В этих шагах предполагается, что вы установили файлы ODAC 18.x в c:\oracle64 и используете файлы Oracle.ManagedDataAccess.dll и Oracle.DataAccess.dll версии 4.122.18.3.

1. На сайте загрузки Oracle установите [64-разрядную версию Oracle ODAC OUI](https://www.oracle.com/technetwork/topics/dotnet/downloads/odacdeploy-4242173.html). 
2. Зарегистрируйте управляемый клиент ODP.NET в глобальном кэше сборок:

    C:\oracle64\product\18.0.0\client_1\odp.net\bin\4\OraProvCfg.exe /action:gac /providerpath:C:\oracle64\product\18.0.0\client_1\odp.net\managed\common\Oracle.ManagedDataAccess.dll
3. Добавьте записи управляемого клиента ODP.NET в файл machine.config:

    C:\oracle64\product\18.0.0\client_1\odp.net\bin\4\OraProvCfg.exe /action:config /force /product:odpm /frameworkversion:v4.0.30319 /productversion:4.122.18.3

### <a name="power-bi-reports-use-unmanaged-odpnet"></a>Отчеты Power BI используют неуправляемый драйвер ODP.NET

Отчеты Power BI используют **неуправляемый драйвер ODP.NET**. Чтобы зарегистрировать неуправляемый драйвер ODP.NET, следуйте приведенным ниже инструкциям.

1. Зарегистрируйте неуправляемый клиент ODP.NET в глобальном кэше сборок:

   C:\oracle64\product\18.0.0\client_1\odp.net\bin\4\OraProvCfg.exe /action:gac /providerpath:C:\oracle64\product\18.0.0\client_1\odp.net\bin\4\Oracle.DataAccess.dll
2. Добавьте записи неуправляемого клиента ODP.NET в файл machine.config:

   C:\oracle64\product\18.0.0\client_1\odp.net\bin\4\OraProvCfg.exe /action:config /force /product:odp /frameworkversion:v4.0.30319 /productversion:4.122.18.3
 
## <a name="32-bit-drivers-for-report-builder"></a>32-разрядные драйверы для построителя отчетов

Построитель отчетов использует **Managed ODP.NET** для создания отчетов с разбивкой на страницы. Следующие шаги необходимы только при использовании драйверов Oracle ODAC 12.2 и более поздних версий, так как они по умолчанию устанавливаются в конфигурацию не на уровне компьютера для новой установки Oracle Home. В этих шагах предполагается, что вы установили файлы ODAC 18.x в c:\oracle32 и используете файл Oracle.ManagedDataAccess.dll версии 4.122.18.3.

1. На сайте загрузки Oracle установите [32-разрядную версию Oracle ODAC OUI](https://www.oracle.com/technetwork/topics/dotnet/downloads/odacdev-4242174.html).
2. Зарегистрируйте управляемый клиент ODP.NET в глобальном кэше сборок:

    C:\oracle32\product\18.0.0\client_1\odp.net\bin\4\OraProvCfg.exe /action:gac /providerpath:C:\oracle32\product\18.0.0\client_1\odp.net\managed\common\Oracle.ManagedDataAccess.dll
3. Добавьте записи управляемого клиента ODP.NET в файл machine.config:

    C:\oracle32\product\18.0.0\client_1\odp.net\bin\4\OraProvCfg.exe /action:config /force /product:odpm /frameworkversion:v4.0.30319 /productversion:4.122.18.3

## <a name="64-bit-and-32-bit-drivers-for-power-bi-desktop"></a>64-разрядные и 32-разрядные драйверы для Power BI Desktop

Отчеты Power BI используют **неуправляемый драйвер ODP.NET**. Следующие шаги необходимы только при использовании драйверов Oracle ODAC 12.2 и более поздних версий, так как они по умолчанию устанавливаются в конфигурацию не на уровне компьютера для новой установки Oracle Home. В этих шагах предполагается, что вы установили файлы ODAC 18.x в c:\oracle64 для 64-разрядной версии и в c:\oracle32 для 32-разрядной версии и используете файл Oracle.DataAccess.dll версии 4.122.18.3. Чтобы зарегистрировать неуправляемый драйвер ODP.NET, следуйте приведенным ниже инструкциям.

### <a name="64-bit-power-bi-desktop"></a>64-разрядная версия Power BI Desktop

1. Зарегистрируйте неуправляемый клиент ODP.NET в глобальном кэше сборок:

   C:\oracle64\product\18.0.0\client_1\odp.net\bin\4\OraProvCfg.exe /action:gac /providerpath:C:\oracle64\product\18.0.0\client_1\odp.net\bin\4\Oracle.DataAccess.dll
2. Добавьте записи неуправляемого клиента ODP.NET в файл machine.config:

   C:\oracle64\product\18.0.0\client_1\odp.net\bin\4\OraProvCfg.exe /action:config /force /product:odp /frameworkversion:v4.0.30319 /productversion:4.122.18.3

### <a name="32-bit-power-bi-desktop"></a>32-разрядная версия Power BI Desktop

1. Зарегистрируйте неуправляемый клиент ODP.NET в глобальном кэше сборок:

   C:\oracle32\product\18.0.0\client_1\odp.net\bin\4\OraProvCfg.exe /action:gac /providerpath:C:\oracle32\product\18.0.0\client_1\odp.net\bin\4\Oracle.DataAccess.dll
2. Добавьте записи неуправляемого клиента ODP.NET в файл machine.config:

   C:\oracle32\product\18.0.0\client_1\odp.net\bin\4\OraProvCfg.exe /action:config /force /product:odp /frameworkversion:v4.0.30319 /productversion:4.122.18.3
  
##  <a name="connection-string"></a><a name="Connection"></a> Строка подключения  
 Данные для строки соединения и учетные данные для подключения к источнику данных можно получить у администратора базы данных. В следующем примере строки соединения указывается база данных Oracle на сервере Oracle18 с использованием Юникода. Имя сервера должно соответствовать значению, определенному в файле конфигурации tnsnames.ora в качестве имени экземпляра сервера Oracle.  
  
```  
Data Source="Oracle"; Unicode="True"  
```  
  
 Дополнительные сведения о примерах строк подключения см. в статье [Create data connection strings - Report Builder & SSRS](../../reporting-services/report-data/data-connections-data-sources-and-connection-strings-report-builder-and-ssrs.md) (Создание строк подключения к данным (построитель отчетов и службы SSRS))  
  
##  <a name="credentials"></a><a name="Credentials"></a> Учетные данные  
 Учетные данные необходимы для запуска запросов, локального предварительного просмотра отчетов, а также для предварительного просмотра отчетов на сервере отчетов.  
  
 После публикации отчета может понадобиться изменить учетные данные источника данных, чтобы разрешения, необходимые для получения данных при запуске отчета на сервере отчетов, были допустимыми.  
  
 Дополнительные сведения см. в статье [Задание учетных данных и сведениях о соединении для источников данных отчета](specify-credential-and-connection-information-for-report-data-sources.md).  
  
  
##  <a name="queries"></a><a name="Query"></a> Запросы  
 Для создания набора данных можно выбрать хранимую процедуру из раскрывающегося списка или создать SQL-запрос. Чтобы построить запрос, воспользуйтесь текстовым конструктором запросов. Дополнительные сведения см. в разделе [Пользовательский интерфейс текстового конструктора запросов (построитель отчетов)](../../reporting-services/report-data/text-based-query-designer-user-interface-report-builder.md).  
  
 Можно указать хранимые процедуры, возвращающие только один результирующий набор. Использование курсорных запросов не поддерживается.  
  
##  <a name="parameters"></a><a name="Parameters"></a> Параметры  
 Если запрос включает переменные запроса, то автоматически создаются соответствующие параметры отчета. Этот модуль поддерживает именованные параметры. Oracle версии 9 или более поздней поддерживает параметры с несколькими значениями.  
  
 Параметры отчета создаются со значениями свойств по умолчанию, которые, возможно, потребуется изменить. Например, все параметры отчета имеют тип данных **Text**. После создания параметров отчета можно изменить значения по умолчанию. Дополнительные сведения см. в разделе [Параметры отчета (построитель отчетов и конструктор отчетов)](../../reporting-services/report-design/report-parameters-report-builder-and-report-designer.md).  
  
  
##  <a name="remarks"></a><a name="Remarks"></a> Замечания  
 Прежде чем подключиться к источнику данных Oracle, системный администратор должен установить версию поставщика данных .NET для Oracle, поддерживающую получение данных из базы данных Oracle. Этот поставщик данных должен быть установлен на компьютере, где работает построитель отчетов, а также на сервере отчетов.  
  
 Дополнительные сведения см. в следующих статьях:  
  
-   [Как использовать службы Reporting Services для настройки и доступа к источнику данных Oracle](/archive/blogs/dataaccesstechnologies/configure-oracle-data-source-for-sql-server-reporting-services-ssdt-and-report-server)  
-   [Как добавить разрешения для субъекта безопасности NETWORK SERVICE](https://support.microsoft.com/kb/870668)  
  
### <a name="alternate-data-extensions"></a>Альтернативные модули обработки данных 
 
 Также данные из базы данных Oracle можно получить с помощью источника данных OLE DB. Дополнительные сведения см. в разделе [Тип соединения OLE DB (службы SSRS)](../../reporting-services/report-data/ole-db-connection-type-ssrs.md).  

::: moniker range=">=sql-server-2017||=sqlallproducts-allversions" 
### <a name="report-models"></a>Модели отчетов  

 Также можно создавать модели на основе базы данных Oracle.  
::: moniker-end
   
### <a name="platform-and-version-information"></a>Сведения о платформе и версии  

 Дополнительные сведения о поддержке платформ и версий см. в статье [Источники данных, поддерживаемые службами Reporting Services (SSRS)](../../reporting-services/report-data/data-sources-supported-by-reporting-services-ssrs.md).  

  
## <a name="see-also"></a>См. также:

 [Параметры отчета (построитель отчетов и конструктор отчетов)](../../reporting-services/report-design/report-parameters-report-builder-and-report-designer.md)   
 [Фильтрация, группирование и сортировка данных (построитель отчетов и службы SSRS)](../../reporting-services/report-design/filter-group-and-sort-data-report-builder-and-ssrs.md)   
 [Выражения (построитель отчетов и службы SSRS)](../../reporting-services/report-design/expressions-report-builder-and-ssrs.md)  
  
