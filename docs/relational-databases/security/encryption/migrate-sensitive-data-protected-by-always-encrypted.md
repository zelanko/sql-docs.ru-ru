---
title: Массовая загрузка зашифрованных данных в столбцы с помощью Always Encrypted
description: Узнайте, как выполнять массовую загрузку данных в столбцы с помощью Always Encrypted с использованием SQL Server.
ms.custom: seo-lt-2019
ms.date: 11/04/2015
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: vanto
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- Always Encrypted, bulk import
ms.assetid: b2ca08ed-a927-40fb-9059-09496752595e
author: jaszymas
ms.author: jaszymas
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: b96529feb6e6e4c4ac2ad7d4be62474a624392d8
ms.sourcegitcommit: b2e81cb349eecacee91cd3766410ffb3677ad7e2
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/01/2020
ms.locfileid: "76909914"
---
# <a name="bulk-load-encrypted-data-to-columns-using-always-encrypted"></a>Массовая загрузка зашифрованных данных в столбцы с помощью Always Encrypted
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]

Чтобы во время операций массового копирования загрузить зашифрованные данные, не проверяя метаданные на сервере, создайте пользователя с параметром **ALLOW_ENCRYPTED_VALUE_MODIFICATIONS** . Этот параметр предназначен для устаревших средств или сторонних рабочих процессов извлечения, преобразования и загрузки (ETL), которые не могут использовать функцию Always Encrypted. Таким образом пользователи могут безопасно перемещать зашифрованные данные из одного набора таблиц, содержащего зашифрованные столбцы, в другой набор таблиц с зашифрованными столбцами (в той же или другой базе данных).  

 ## <a name="the-allow_encrypted_value_modifications-option"></a>Параметр ALLOW_ENCRYPTED_VALUE_MODIFICATIONS  
 Команды [CREATE USER](../../../t-sql/statements/create-user-transact-sql.md) и [ALTER USER](../../../t-sql/statements/alter-user-transact-sql.md) имеют параметр ALLOW_ENCRYPTED_VALUE_MODIFICATIONS. Если задано значение ON (значение по умолчанию — OFF), этот параметр отключает проверки шифрованных метаданных на сервере в операциях массового копирования, что позволяет пользователю массово копировать зашифрованные данные из одной таблицы или базы данных в другую и при этом не расшифровывать данные.  
  
## <a name="data-migration-scenarios"></a>Сценарии переноса данных  
В таблице ниже показаны рекомендуемые параметры, подходящие для нескольких сценариев переноса.  
 
![always-encrypted-migration](../../../relational-databases/security/encryption/media/always-encrypted-migration.PNG "always-encrypted-migration")  

## <a name="bulk-loading-of-encrypted-data"></a>Массовая загрузка зашифрованных данных  
Загружайте зашифрованные данные с помощью такого процесса:  

1.  Присвойте параметру значение ON для пользователя в базе данных, в которую массово копируются данные. Пример:  
 
   ```  
    ALTER USER Bob WITH ALLOW_ENCRYPTED_VALUE_MODIFICATIONS = ON;  
   ```  

2.  Подключившись, как этот пользователь, запустите приложение или средство массового копирования. (Если приложение использует драйвер клиента с включенным постоянным шифрованием, убедитесь, что строка подключения для источника данных не содержит параметр **column encryption setting=enabled** , который оставляет зашифрованными данные, извлеченные из зашифрованных столбцов. Дополнительные сведения см. в разделе [Разработка приложений с помощью Always Encrypted](always-encrypted-client-development.md).)  
  
3.  Снова задайте для параметра ALLOW_ENCRYPTED_VALUE_MODIFICATIONS значение OFF. Пример:  

    ```  
    ALTER USER Bob WITH ALLOW_ENCRYPTED_VALUE_MODIFICATIONS = OFF;  
    ```  

## <a name="potential-for-data-corruption"></a>Возможное повреждение данных  
Неправильное использование этого параметра может привести к повреждению данных. Параметр **ALLOW_ENCRYPTED_VALUE_MODIFICATIONS** позволяет пользователю вставлять данные в зашифрованные столбцы в базе данных, в том числе данные, зашифрованные с помощью разных ключей, неверно зашифрованные данные и данные, которые вообще не зашифрованы. Если пользователь случайно копирует данные, которые неправильно зашифрованы с помощью схемы шифрования (ключ шифрования столбца, алгоритм, тип шифрования), настроенной для целевого столбца, вы не сможете расшифровать эти данные (они будут повреждены). Этот параметр следует использовать осторожно, так как он может повредить данные в базе данных.  

Приведенный ниже сценарий демонстрирует, как неправильный импорт данных может привести к их повреждению:  

1.  Для пользователя задано значение ON для этого параметра.  
 
2.  Пользователь запускает приложение, которое подключается к базе данных. Приложение с помощью массовых API-интерфейсов вставляет обычные текстовые значения в зашифрованные столбцы. Приложение ожидает, что драйвер клиента с включенным постоянным шифрованием зашифрует данные при вставке. Но приложение настроено неправильно, поэтому или оно использует драйвер, не поддерживающий постоянное шифрование, или строка подключения не содержит параметр **column encryption setting=enabled**.  

3.  Приложение отправляет обычные текстовые значения на сервер. Так как проверки зашифрованных метаданных на сервере отключены для пользователя, сервер позволяет вставлять в зашифрованный столбец недопустимые данные (открытый текст вместо зашифрованных данных).  
 
4.  То же или другое приложение подключается к базе данных с помощью драйвера с включенным постоянным шифрованием и параметром **column encryption setting=enabled** в строке подключения, а затем извлекает данные. Приложение ожидает, что драйвер расшифрует данные. Но драйверу это не удается, так как данные зашифрованы неверно.  

## <a name="best-practice"></a>Рекомендации  
 
Используйте назначенные учетные записи пользователя для долговременных рабочих нагрузок, использующих этот параметр.  
 
Работая с кратковременно работающими приложениями или средствами массового копирования, которым нужно переместить зашифрованные данные, но не нужно их расшифровывать, задавайте для параметра значение ON непосредственно перед запуском приложения, возвращая значение OFF сразу после запуска операции.  
 
Не разрабатывайте новые приложения с помощью этого параметра. Вместо этого используйте драйвер клиента, который предоставляет API для подавления проверок криптографических метаданных для одного сеанса, например параметр AllowEncryptedValueModifications в поставщике данных .NET Framework для SQL Server — см. [Копирование зашифрованных данных с помощью SqlBulkCopy](develop-using-always-encrypted-with-net-framework-data-provider.md#copying-encrypted-data-using-sqlbulkcopy). 

## <a name="next-steps"></a>Next Steps
- [Выполнение запросов к столбцам с помощью Always Encrypted с использованием SQL Server Management Studio](always-encrypted-query-columns-ssms.md)
- [Разработка приложений с помощью Always Encrypted](always-encrypted-client-development.md)

## <a name="see-also"></a>См. также:  
- [Always Encrypted](../../../relational-databases/security/encryption/always-encrypted-database-engine.md)
- [Перенос данных в столбцы или из них с помощью Always Encrypted с использованием мастера импорта и экспорта SQL Server](always-encrypted-migrate-using-import-export-wizard.md)
- [CREATE USER (Transact-SQL)](../../../t-sql/statements/create-user-transact-sql.md)   
- [ALTER USER (Transact-SQL)](../../../t-sql/statements/alter-user-transact-sql.md)   

