---
title: Замыкание соединения на SQL Server из скрипта Python или R
description: Узнайте, как использовать обратное соединение для подключения к SQL Server через ODBC для чтения или записи данных из скрипта Python или R, выполняемого из sp_execute_external_script. Его можно использовать, если нельзя использовать аргументы InputDataSet и OutputDataSet sp_execute_external_script.
ms.prod: sql
ms.technology: machine-learning
ms.date: 08/21/2019
ms.topic: conceptual
author: Aniruddh25
ms.author: anmunde
ms.reviewer: dphansen
monikerRange: '>=sql-server-ver15||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 62b4ce483df2d38e5e2549d054c02b6c797837f3
ms.sourcegitcommit: 5e838bdf705136f34d4d8b622740b0e643cb8d96
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/20/2019
ms.locfileid: "69657491"
---
# <a name="loopback-connection-to-sql-server-from-a-python-or-r-script"></a>Замыкание соединения на SQL Server из скрипта Python или R
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

Узнайте, как использовать обратное соединение для подключения к SQL Server через [ODBC](../../connect/odbc/microsoft-odbc-driver-for-sql-server.md) для чтения или записи данных из скрипта Python или R, выполняемого `sp_execute_external_script`из. Его можно использовать при использовании аргументов `sp_execute_external_script` **InputDataSet** и **OutputDataSet** в невозможности.

## <a name="connection-string"></a>Строка соединения

Чтобы установить обратное соединение, необходимо использовать правильную строку подключения. Общие обязательные аргументы — это имя [драйвера ODBC](../../connect/odbc/microsoft-odbc-driver-for-sql-server.md), адрес сервера и имя базы данных.

### <a name="connection-string-on-windows"></a>Строка подключения в Windows

Для проверки подлинности SQL Server в Windows скрипт Python или R может использовать атрибут строки подключения **Trusted_Connection** для проверки подлинности в качестве того же пользователя, запустившего sp_execute_external_script.

Ниже приведен пример строки подключения замыкания на себя в Windows:

``` 
"Driver=SQL Server;Server=.;Database=nameOfDatabase;Trusted_Connection=Yes;"
```

### <a name="connection-string-on-linux"></a>Строка подключения в Linux

Для проверки подлинности на SQL Server на Linux сценарий Python или R должен использовать атрибуты **clientcertificate** и **ClientKey** драйвера ODBC для проверки подлинности как того же пользователя, `sp_execute_external_script`который выполнялся. Для этого необходимо использовать [последнюю версию драйвера ODBC](../../connect/odbc/download-odbc-driver-for-sql-server.md) 17.4.1.1.

Ниже приведен пример строки подключения замыкания на себя в Linux:

```
"Driver=ODBC Driver 17 for SQL Server;Server=fe80::8012:3df5:0:5db1%eth0;Database=nameOfDatabase;ClientCertificate=file:/var/opt/mssql-extensibility/data/baeaac72-60b3-4fae-acfd-c50eff5d34a2/sqlsatellitecert.pem;ClientKey=file:/var/opt/mssql-extensibility/data/baeaac72-60b3-4fae-acfd-c50eff5d34a2/sqlsatellitekey.pem;TrustServerCertificate=Yes;Trusted_Connection=no;Encrypt=Yes"
```

Адрес сервера, расположение файла сертификата клиента и расположение файла ключа клиента уникальны для всех `sp_execute_external_script` и могут быть получены с помощью API **rx_get_sql_loopback_connection_string ()** для Python или  **Рксжетскллупбаккконнектионстринг ()** для R.

Дополнительные сведения об атрибутах строки подключения см. в разделе имена [DSN и ключевые слова и атрибуты строки подключения](https://docs.microsoft.com/sql/connect/odbc/dsn-connection-string-attribute?view=sql-server-linux-ver15#new-connection-string-keywords-and-connection-attributes) для Microsoft ODBC Driver for SQL Server.

## <a name="generate-connection-string-with-revoscalepy-for-python"></a>Создание строки подключения с помощью revoscalepy для Python

Вы можете использовать API **rx_get_sql_loopback_connection_string ()** в [revoscalepy](../python/ref-py-revoscalepy.md) , чтобы создать правильную строку подключения для подключения замыкания на себя в скрипте Python.

Он принимает следующие аргументы:

| Аргумент | Описание |
|-|-|
| name_of_database | Имя базы данных, в которую должно быть установлено соединение |
| odbc_driver | Имя драйвера ODBC |

### <a name="examples"></a>Примеры

Пример для SQL Server в Windows:

```sql
EXECUTE sp_execute_external_script
@language = N'Python',
@script = N'
from revoscalepy import rx_get_sql_loopback_connection_string, RxSqlServerData, rx_data_step
loopback_connection_string = rx_get_sql_loopback_connection_string(odbc_driver="SQL Server", name_of_database="DBName")
print("Connection String:{0}".format(loopback_connection_string))
data_set = RxSqlServerData(sql_query = "select col1, col2 from tableName",
                           connection_string = loopback_connection_string)
OutputDataSet = rx_data_step(data_set)
'
WITH RESULT SETS ((col1 int, col2 int))
GO
```

Пример для SQL Server на Linux:

```sql
EXECUTE sp_execute_external_script
@language = N'Python',
@script = N'
from revoscalepy import rx_get_sql_loopback_connection_string, RxSqlServerData, rx_data_step
loopback_connection_string = rx_get_sql_loopback_connection_string(odbc_driver="ODBC Driver 17 for SQL Server",
                                                                   name_of_database="DBName")
print("Loopback Connection String:{0}".format(loopback_connection_string))
data_set = RxSqlServerData(sql_query = "select col1, col2 from tableName",
                           connection_string = loopback_connection_string)
OutputDataSet = rx_data_step(data_set)
'
WITH RESULT SETS ((col1 int, col2 int))
GO
```

## <a name="generate-connection-string-with-revoscaler-for-r"></a>Создание строки подключения с помощью RevoScaleR для R

Вы можете использовать API **рксжетскллупбаккконнектионстринг ()** в [RevoScaleR](../r/ref-r-revoscaler.md) , чтобы создать правильную строку подключения для подключения замыкания на себя в скрипте R.

Он принимает следующие аргументы:

| Аргумент | Описание |
|-|-|
| намеофдатабасе | Имя базы данных, в которую должно быть установлено соединение |
| одбкдривер | Имя драйвера ODBC |

### <a name="examples"></a>Примеры

Пример для SQL Server в Windows:

```sql
EXECUTE sp_execute_external_script
@language = N'R',
@script = N'
    loopbackConnectionString <- rxGetSqlLoopbackConnectionString(nameOfDatabase="DBName", odbcDriver ="SQL Server")
    print(paste("Connection String:", loopbackConnectionString))
    dataSet <- RxSqlServerData(sqlQuery = "select col1, col2 from tableName",
                               connectionString = loopbackConnectionString)
    OutputDataSet <- rxDataStep(dataSet)
'
WITH RESULT SETS ((col1 int, col2 int))
GO
```

Пример для SQL Server на Linux:

```sql
EXECUTE sp_execute_external_script
@language = N'R',
@script = N'
    loopbackConnectionString <-  rxGetSqlLoopbackConnectionString(nameOfDatabase="DBName", 
                                                                  odbcDriver ="ODBC Driver 17 for SQL Server")
    print(paste("Connection String:", loopbackConnectionString))
    dataSet <- RxSqlServerData(sqlQuery = "select col1, col2 from tableName", 
                               connectionString = loopbackConnectionString)
    OutputDataSet <- rxDataStep(dataSet)
'
WITH RESULT SETS ((col1 int, col2 int))
GO
```

## <a name="next-steps"></a>Следующие шаги

+ [Драйвер Microsoft ODBC для SQL Server](../../connect/odbc/microsoft-odbc-driver-for-sql-server.md)
+ [revoscalepy](../python/ref-py-revoscalepy.md)
+ [RevoScaleR](../r/ref-r-revoscaler.md)
