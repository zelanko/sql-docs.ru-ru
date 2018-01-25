---
title: "Создание конечной ТОЧКИ (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 08/10/2017
ms.prod: sql-non-specified
ms.prod_service: sql-database
ms.service: 
ms.component: t-sql|statements
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- ENDPOINT
- CREATE ENDPOINT
- ENDPOINT_TSQL
- CREATE_ENDPOINT_TSQL
dev_langs: TSQL
helpviewer_keywords:
- database mirroring [SQL Server], endpoint
- HTTP SOAP support [SQL Server]
- CREATE ENDPOINT statement
- Availability Groups [SQL Server], configuring
- endpoints [SQL Server], creating
- SOAP [SQL Server built-in support], endpoints
- SOAP [SQL Server built-in support], sqlbatch
- DATABASE_MIRRORING option
- HTTP protocol option [SQL Server]
- SOAP [SQL Server built-in support], ad hoc
- TCP protocol option [SQL Server]
- SERVICE_BROKER option
- Availability Groups [SQL Server], endpoint
ms.assetid: 6405e7ec-0b5b-4afd-9792-1bfa5a2491f6
caps.latest.revision: "135"
author: barbkess
ms.author: barbkess
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: c1d87ac5214da9a3458cdffd41bdd457a433afab
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2018
---
# <a name="create-endpoint-transact-sql"></a>CREATE ENDPOINT (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Создает конечные точки и определяет их параметры, включая методы, доступные клиентским приложениям. Разрешений, связанных с Подробнее [GRANT, предоставление разрешений конечной точке &#40; Transact-SQL &#41; ](../../t-sql/statements/grant-endpoint-permissions-transact-sql.md).  
  
 Синтаксис CREATE ENDPOINT логически может быть разбит на две части.  
  
-   Первая часть начинается с AS и заканчивается перед предложением FOR.  
  
     В этой части задаются сведения, связанные с транспортным протоколом (TCP), устанавливается номер прослушиваемого порта для конечной точки, а также указывается метод проверки подлинности конечной точки и/или список IP-адресов (при наличии), доступ к конечной точке от которых нужно запретить.  
  
-   Вторая часть начинается с предложения FOR.  
  
     В этой части определяется, какие полезные данные будут поддерживаться конечной точкой. Полезная нагрузка может принимать одно из поддерживаемых типов: [!INCLUDE[tsql](../../includes/tsql-md.md)], компонент service broker, зеркальное отображение базы данных. В эту часть также включаются сведения, зависящие от выбранного типа.  
  
> **Примечание:** собственных веб-служб XML (конечные точки SOAP/HTTP) был удален в [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)].  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
CREATE ENDPOINT endPointName [ AUTHORIZATION login ]  
[ STATE = { STARTED | STOPPED | DISABLED } ]  
AS { TCP } (  
   <protocol_specific_arguments>  
        )  
FOR { TSQL | SERVICE_BROKER | DATABASE_MIRRORING } (  
   <language_specific_arguments>  
        )  
  
<AS TCP_protocol_specific_arguments> ::=  
AS TCP (  
  LISTENER_PORT = listenerPort  
  [ [ , ] LISTENER_IP = ALL | ( 4-part-ip ) | ( "ip_address_v6" ) ]  
  
)  
  
<FOR SERVICE_BROKER_language_specific_arguments> ::=  
FOR SERVICE_BROKER (  
   [ AUTHENTICATION = {   
            WINDOWS [ { NTLM | KERBEROS | NEGOTIATE } ]   
      | CERTIFICATE certificate_name   
      | WINDOWS [ { NTLM | KERBEROS | NEGOTIATE } ] CERTIFICATE certificate_name   
      | CERTIFICATE certificate_name WINDOWS [ { NTLM | KERBEROS | NEGOTIATE } ]   
    } ]  
   [ [ , ] ENCRYPTION = { DISABLED | { { SUPPORTED | REQUIRED }   
       [ ALGORITHM { AES | RC4 | AES RC4 | RC4 AES } ] }   
   ]  
   [ [ , ] MESSAGE_FORWARDING = { ENABLED | DISABLED } ]  
   [ [ , ] MESSAGE_FORWARD_SIZE = forward_size ]  
)  
  

<FOR DATABASE_MIRRORING_language_specific_arguments> ::=  
FOR DATABASE_MIRRORING (  
   [ AUTHENTICATION = {   
            WINDOWS [ { NTLM | KERBEROS | NEGOTIATE } ]   
      | CERTIFICATE certificate_name   
      | WINDOWS [ { NTLM | KERBEROS | NEGOTIATE } ] CERTIFICATE certificate_name   
      | CERTIFICATE certificate_name WINDOWS [ { NTLM | KERBEROS | NEGOTIATE } ]   
   [ [ [ , ] ] ENCRYPTION = { DISABLED | { { SUPPORTED | REQUIRED }   
       [ ALGORITHM { AES | RC4 | AES RC4 | RC4 AES } ] }   
  
    ]   
   [ , ] ROLE = { WITNESS | PARTNER | ALL }  
)  
```  
  
## <a name="arguments"></a>Аргументы  
 *endPointName*  
 Назначенное имя создаваемой конечной точки. Используется при обновлении или удалении конечной точки.  
  
 АВТОРИЗАЦИЯ *входа*  
 Указывает правильное имя входа [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] или Windows, которое назначается владельцем только что созданного объекта конечной точки. Если аргумент AUTHORIZATION не указан, по умолчанию владельцем только что созданного объекта становится пользователь, вызывающий инструкцию.  
  
 Назначить владельца при помощи аргумента AUTHORIZATION, вызывающий объект должен иметь разрешение IMPERSONATE на указанного *входа*.  
  
 Изменить владельца, в разделе [ALTER ENDPOINT &#40; Transact-SQL &#41; ](../../t-sql/statements/alter-endpoint-transact-sql.md).  
  
 СОСТОЯНИЕ  **=**  {STARTED | **ОСТАНОВЛЕНА** | ОТКЛЮЧЕННЫЕ}  
 Состояние конечной точки после ее создания. Если при создании конечной точки состояние не указано, по умолчанию устанавливается значение STOPPED.  
  
 STARTED  
 Конечная точка запущена и активно прослушивает соответствующий порт, ожидая соединений.  
  
 DISABLED  
 Конечная точка отключена. В этом состоянии сервер прослушивает запросы к порту, но возвращает клиенту ошибку.  
  
 **ОСТАНОВЛЕНА**  
 Конечная точка остановлена. В этом состоянии сервер не прослушивает порт конечной точки и не отвечает ни на какие попытки запроса на использование конечной точки.  
  
 Чтобы изменить состояние, используйте [ALTER ENDPOINT &#40; Transact-SQL &#41; ](../../t-sql/statements/alter-endpoint-transact-sql.md).  
  
 AS { TCP }  
 Указывает используемый транспортный протокол.  
  
 FOR { TSQL | SERVICE_BROKER | DATABASE_MIRRORING }  
 Указывает тип передаваемых полезных данных.  
  
 В настоящее время не существует специфических для языка [!INCLUDE[tsql](../../includes/tsql-md.md)] аргументов, передаваемых в параметре `<language_specific_arguments>`.  
  
 **Параметр протокола TCP**  
  
 Следующие аргументы относятся только к протоколу TCP.  
  
 LISTENER_PORT **=***listenerPort*  
 Указывает номер порта протокола TCP/IP, прослушиваемого компонентом Service Broker на предмет соединений. По соглашению используется порт 4022, но допустим любой порт от 1024 до 32767.  
  
 LISTENER_IP  **=**  все |  **(*** 4 частей ip* **)** | **(** »*ip_address_v6 *» **)**  
 Указывает IP-адрес, с которым конечная точка будет ожидать соединения. По умолчанию значение установлено в ALL. Это значит, что средство прослушивания примет соединение с любым верным IP-адресом.  
  
 Если зеркальное отображение базы данных настраивается с использованием IP-адреса, а не полного имени домена (`ALTER DATABASE SET PARTNER = partner_IP_address` или `ALTER DATABASE SET WITNESS = witness_IP_address`), необходимо указать `LISTENER_IP =IP_address` вместо `LISTENER_IP=ALL` при создании конечных точек зеркального отображения.  
  
 **Аргументы SERVICE_BROKER и DATABASE_MIRRORING**  
  
 Параметры AUTHENTICATION и ENCRYPTION используются, если указан аргумент SERVICE_BROKER или DATABASE_MIRRORING.  
  
> [!NOTE]  
>  Для получения сведений об аргументах, относящихся только к SERVICE_BROKER, см. подраздел «Параметры SERVICE_BROKER» ниже в данном разделе. Для получения сведений о параметрах, относящихся только к DATABASE_MIRRORING, см. статью «Параметры DATABASE_MIRRORING» ниже в данном разделе.  
  
 Проверка ПОДЛИННОСТИ  **=**  \<authentication_options > указывает требования к проверке подлинности TCP/IP для соединений данной конечной точки. По умолчанию значение установлено в WINDOWS.  
  
 Поддерживаемые методы проверки подлинности включают в себя NTLM, Kerberos или оба этих метода.  
  
> [!IMPORTANT]  
>  Все соединения зеркального отображения на экземпляре сервера используют одну конечную точку зеркального отображения базы данных. Любая попытка создания дополнительной конечной точки зеркального отображения баз данных приведет к ошибке.  
  
 **\<authentication_options> ::=**  
  
 **WINDOWS** [{NTLM | KERBEROS | **NEGOTIATE** }]  
 Указывает, что конечная точка будет подключена с использованием протокола проверки подлинности Windows. Это значение по умолчанию.  
  
 Если указать режим авторизации (NTLM или KERBEROS), этот метод всегда будет использоваться в качестве протокола проверки подлинности. Значение по умолчанию NEGOTIATE соответствует тому, что конечная точка будет использовать протокол переговоров Windows для выбора NTLM или Kerberos.  
  
 СЕРТИФИКАТ *имя_сертификата*  
 Указывает, что конечная точка для проверки подлинности подключения, с помощью сертификата, заданного свойством *имя_сертификата* для определения идентификатора для авторизации. Противоположная конечная точка должна иметь сертификат с открытым ключом, совпадающим с закрытым ключом указанного сертификата.  
  
 WINDOWS [{NTLM | KERBEROS | **NEGOTIATE** }] СЕРТИФИКАТ *имя_сертификата*  
 Указывает на то, что конечная точка будет производить попытки подключения при помощи проверки подлинности Windows и, в случае неудачи, будет пытаться использовать указанный сертификат.  
  
 СЕРТИФИКАТ *имя_сертификата* WINDOWS [{NTLM | KERBEROS | **NEGOTIATE** }]  
 Указывает на то, что конечная точка будет производить попытки подключения при помощи указанного сертификата и, в случае неуспеха, будет пытаться использовать проверку подлинности Windows.  
  
 ШИФРОВАНИЕ = {ОТКЛЮЧЕННЫЕ | ПОДДЕРЖИВАЕТСЯ | **REQUIRED** } [АЛГОРИТМ { **AES** | RC4 | АЛГОРИТМ AES RC4 | RC4 AES}]  
 Указывает, будет ли использоваться шифрование в процессе. По умолчанию значение установлено в REQUIRED.  
  
 DISABLED  
 Указывает на то, что данные, передаваемые через соединение, не будут зашифрованы.  
  
 SUPPORTED  
 Указывает на то, что данные будут зашифрованы только в случае, если у противоположной конечной точки этот аргумент принял значение SUPPORTED или REQUIRED.  
  
 REQUIRED  
 Указывает на то, что соединение с этой конечной точкой должно использовать шифрование. Поэтому для подключения к конечной точке значение аргумента ENCRYPTION противоположной конечной точки должно быть установлено в значение SUPPORTED или значение REQUIRED.  
  
 При необходимости можно использовать аргумент ALGORITHM для указания формы шифрования на конечной точке, как показано ниже:  
  
 **AES**  
 Указывает на то, что конечная точка должна использовать алгоритм AES. Это значение по умолчанию в [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] и более поздних версий.  
  
 RC4  
 Указывает на то, что конечная точка должна использовать алгоритм RC4. Это значение по умолчанию через [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)].  
  
> [!NOTE]  
>  Алгоритм RC4 поддерживается только в целях обратной совместимости. Когда база данных имеет уровень совместимости 90 или 100, новые материалы могут шифроваться только с помощью алгоритмов RC4 или RC4_128. (Не рекомендуется.) Используйте вместо этого более новые алгоритмы, например AES. В [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] и более поздних версиях материалы, зашифрованные с помощью алгоритмов RC4 или RC4_128, могут быть расшифрованы на любом уровне совместимости.  
  
 AES RC4  
 Указывает на то, что две конечные точки будут согласовывать алгоритм шифрования, оставляя приоритет за алгоритмом AES.  
  
 RC4 AES  
 Указывает на то, что две конечные точки будут согласовывать алгоритм шифрования, оставляя приоритет за алгоритмом RC4.  
  
> [!NOTE]  
>  Алгоритм RC4 устарел. [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)] Вместо этого рекомендуется использовать алгоритм AES.  
  
 Если обе конечные точки указывают оба алгоритма, но в разной последовательности, то используется та, которая указана на принимающей стороне.  
  
 **Параметры SERVICE_BROKER**  
  
 Следующие параметры используются, если указан аргумент SERVICE_BROKER.  
  
 MESSAGE_FORWARDING  **=**  {ВКЛЮЧЕНО | **ОТКЛЮЧЕНО** }  
 Определяет, будут ли перенаправлены сообщения, полученные конечной точкой и предназначенные для служб, расположенных в других местах.  
  
 ENABLED  
 Перенаправляет сообщения, если доступен адрес перенаправления.  
  
 DISABLED  
 Удаляет сообщения, предназначенные для служб, расположенных в других местах. Это значение по умолчанию.  
  
 MESSAGE_FORWARD_SIZE **= *** forward_size*  
 Указывает максимальный объем хранилища в мегабайтах для размещения в нем сообщений конечной точки, предназначенных для перенаправления.  
  
 **Параметры DATABASE_MIRRORING**  
  
 Следующие параметры используются, если указан аргумент DATABASE_MIRRORING.  
  
 РОЛЬ  **=**  {СЛЕДЯЩИЙ СЕРВЕР | PARTNER | ALL}  
 Указывает роль в зеркальном отображении базы данных или роли, поддерживаемые конечной точкой.  
  
 WITNESS  
 Позволяет конечной точке выполнять роль следящего сервера в процессе зеркального отображения.  
  
> [!NOTE]  
>  Для выпуска [!INCLUDE[ssExpressEd2005](../../includes/ssexpressed2005-md.md)] WITNESS является единственным доступным значением.  
  
 PARTNER  
 Позволяет конечной точке выполнять роль участника в процессе зеркального отображения.  
  
 ALL  
 Позволяет конечной точке выполнять как роль следящего сервера, так и роль участника в процессе зеркального отображения.  
  
 Дополнительные сведения об этих ролях см. в разделе [зеркального отображения базы данных &#40; SQL Server &#41; ](../../database-engine/database-mirroring/database-mirroring-sql-server.md).  
  
> [!NOTE]  
>  Также для аргумента DATABASE_MIRRORING не определен порт по умолчанию.  
  
## <a name="remarks"></a>Remarks  
 Инструкции DDL ENDPOINT не могут выполняться внутри пользовательской транзакции. Инструкции ENDPOINT DDL не будут вызывать ошибки даже в случае, если активная транзакция уровня изоляции моментального снимка использует изменяемую конечную точку.  
  
 Запросы к объекту ENDPOINT могут быть выполнены следующими пользователями:  
  
-   Члены **sysadmin** предопределенной роли сервера  
  
-   владельцем конечной точки;  
  
-   пользователями или группами, которым предоставлено разрешение CONNECT на конечную точку.  
  
## <a name="permissions"></a>Разрешения  
 Требуется разрешение CREATE ENDPOINT или членство в предопределенной роли сервера **sysadmin** . Дополнительные сведения см. в разделе [GRANT Endpoint Permissions &#40;Transact-SQL&#41;](../../t-sql/statements/grant-endpoint-permissions-transact-sql.md).  
  
## <a name="example"></a>Пример  
  
### <a name="creating-a-database-mirroring-endpoint"></a>Создание конечной точки зеркального отображения базы данных  
 В следующем примере создается конечная точка зеркального отображения базы данных. Конечная точка использует номер порта `7022`, хотя допустим любой доступный номер порта. Конечная точка настроена на использование проверки подлинности Windows только по методу Kerberos. Аргумент `ENCRYPTION` имеет значение `SUPPORTED`, отличное от значения по умолчанию, для передачи зашифрованных или незашифрованных данных. Конечная точка может выступать как в роли участника, так и в роли следящего сервера.  
  
```  
CREATE ENDPOINT endpoint_mirroring  
    STATE = STARTED  
    AS TCP ( LISTENER_PORT = 7022 )  
    FOR DATABASE_MIRRORING (  
       AUTHENTICATION = WINDOWS KERBEROS,  
       ENCRYPTION = SUPPORTED,  
       ROLE=ALL);  
GO  
```  
  
## <a name="see-also"></a>См. также:  
 [ALTER ENDPOINT (Transact-SQL)](../../t-sql/statements/alter-endpoint-transact-sql.md)   
 [Выбор алгоритма шифрования](../../relational-databases/security/encryption/choose-an-encryption-algorithm.md)   
 [DROP ENDPOINT &#40; Transact-SQL &#41;](../../t-sql/statements/drop-endpoint-transact-sql.md)   
 [EVENTDATA (Transact-SQL)](../../t-sql/functions/eventdata-transact-sql.md)  
  
  

