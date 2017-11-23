---
title: "ALTER ENDPOINT (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 03/06/2017
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
- ALTER ENDPOINT
- ALTER_ENDPOINT_TSQL
dev_langs: TSQL
helpviewer_keywords:
- ALTER ENDPOINT statement
- modifying endpoints
- endpoints [SQL Server], modifying
ms.assetid: 70f35566-30cf-47c6-8394-dfe5d71629d3
caps.latest.revision: "56"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: a035e71325993e088b9910d6538c8bdd61e03f7e
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="alter-endpoint-transact-sql"></a>ALTER ENDPOINT (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2014-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2014-xxxx-xxxx-xxx-md.md)]

  Эта инструкция позволяет изменять существующие конечные точки следующими способами.  
  
-   Путем добавления нового метода к существующей конечной точке.  
  
-   Путем изменения или удаления существующего метода из конечной точки.  
  
-   Путем изменения свойств конечной точки.  
  
> [!NOTE]  
>  В этом подразделе описаны синтаксис и аргументы, характерные для инструкции ALTER ENDPOINT. Описание аргументов, которые являются общими для CREATE ENDPOINT и ALTER ENDPOINT см. в разделе [CREATE ENDPOINT &#40; Transact-SQL &#41; ](../../t-sql/statements/create-endpoint-transact-sql.md).  
  
 Собственные XML-веб-службы (конечные точки SOAP/HTTP) удалены, начиная с [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]).  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
ALTER ENDPOINT endPointName [ AUTHORIZATION login ]  
[ STATE = { STARTED | STOPPED | DISABLED } ]  
[ AS { TCP } ( <protocol_specific_items> ) ]  
[ FOR { TSQL | SERVICE_BROKER | DATABASE_MIRRORING } (  
   <language_specific_items>  
        ) ]  
  
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
   [ , ENCRYPTION = { DISABLED   
       |   
         {{SUPPORTED | REQUIRED }   
       [ ALGORITHM { RC4 | AES | AES RC4 | RC4 AES } ] }   
   ]  
  
  [ , MESSAGE_FORWARDING = {ENABLED | DISABLED} ]  
  [ , MESSAGE_FORWARD_SIZE = forwardSize  
)  
  
<FOR DATABASE_MIRRORING_language_specific_arguments> ::=  
FOR DATABASE_MIRRORING (  
   [ AUTHENTICATION = {   
      WINDOWS [ { NTLM | KERBEROS | NEGOTIATE } ]  
      | CERTIFICATE certificate_name   
      | WINDOWS [ { NTLM | KERBEROS | NEGOTIATE } ] CERTIFICATE certificate_name   
      | CERTIFICATE certificate_name WINDOWS [ { NTLM | KERBEROS | NEGOTIATE } ]   
    } ]  
   [ , ENCRYPTION = { DISABLED   
       |   
         {{SUPPORTED | REQUIRED }   
       [ ALGORITHM { RC4 | AES | AES RC4 | RC4 AES } ] }   
    ]   
   [ , ] ROLE = { WITNESS | PARTNER | ALL }  
)  
  
```  
  
## <a name="arguments"></a>Аргументы  
  
> [!NOTE]  
>  Следующие аргументы являются характерными для инструкции ALTER ENDPOINT. Описания остальных аргументов см. в разделе [CREATE ENDPOINT &#40; Transact-SQL &#41; ](../../t-sql/statements/create-endpoint-transact-sql.md).  
  
 **AS** { **TCP** }  
 Нельзя изменить протокол транспорта с **ALTER ENDPOINT**.  
  
 **АВТОРИЗАЦИЯ** *входа*  
 **АВТОРИЗАЦИИ** параметр недоступен в **ALTER ENDPOINT**. Владельца можно назначать только в момент создания конечной точки.  
  
 **ДЛЯ** { **TSQL** | **SERVICE_BROKER** | **DATABASE_MIRRORING** }  
 Невозможно изменить тип полезных данных с **ALTER ENDPOINT**.  
  
## <a name="remarks"></a>Замечания  
 При использовании ALTER ENDPOINT укажите только те параметры, которые необходимо обновить. При отсутствии явного изменения все свойства существующей конечной точки остаются прежними.  
  
 Инструкции ENDPOINT DDL внутри пользовательской транзакции выполняться не могут.  
  
 Сведения о выборе алгоритма шифрования для использования с конечной точкой см. в разделе [Выбор алгоритма шифрования](../../relational-databases/security/encryption/choose-an-encryption-algorithm.md).  
  
> [!NOTE]  
>  Алгоритм RC4 поддерживается только в целях обратной совместимости. Когда база данных имеет уровень совместимости 90 или 100, новые материалы могут шифроваться только с помощью алгоритмов RC4 или RC4_128. (Не рекомендуется.) Используйте вместо этого более новые алгоритмы, например AES. В [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] и более поздних версиях материалы, зашифрованные с помощью алгоритмов RC4 или RC4_128, могут быть расшифрованы на любом уровне совместимости.  
>   
>  RC4 — относительно слабый алгоритм, а AES — относительно сильный. Однако AES заметно медленнее RC4. Если приоритет защиты выше скорости, рекомендуется использовать алгоритм AES.  
  
## <a name="permissions"></a>Permissions  
 Пользователь должен быть членом **sysadmin** предопределенной роли сервера, владельцем конечной точки, или разрешение ALTER ANY ENDPOINT.  
  
 Чтобы изменить принадлежность существующей конечной точки, необходимо применить инструкцию ALTER AUTHORIZATION. Дополнительные сведения см. в разделе [ALTER AUTHORIZATION &#40; Transact-SQL &#41; ](../../t-sql/statements/alter-authorization-transact-sql.md).  
  
 Дополнительные сведения см. в разделе [GRANT, предоставление разрешений на конечные точки (Transact-SQL)](../../t-sql/statements/grant-endpoint-permissions-transact-sql.md).  
  
## <a name="see-also"></a>См. также:  
 [DROP ENDPOINT (Transact-SQL)](../../t-sql/statements/drop-endpoint-transact-sql.md)   
 [EVENTDATA (Transact-SQL)](../../t-sql/functions/eventdata-transact-sql.md)  
  
  
