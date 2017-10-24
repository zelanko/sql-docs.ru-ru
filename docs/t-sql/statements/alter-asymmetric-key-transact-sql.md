---
title: "ALTER ASYMMETRIC KEY (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 04/12/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- ALTER_ASYMMETRIC_KEY_TSQL
- ALTER ASYMMETRIC KEY
dev_langs:
- TSQL
helpviewer_keywords:
- ENCRYPTION BY PASSWORD option
- passwords [SQL Server], asymmetric keys
- encryption [SQL Server], asymmetric keys
- DECRYPTION BY PASSWORD option
- ALTER ASYMMETRIC KEY statement
- asymmetric keys [SQL Server], modifying
ms.assetid: 958e95d6-fbe6-43e8-abbd-ccedbac2dbac
caps.latest.revision: 29
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 81ae1caa65cac678ecd1ddeef0326d68e291ba36
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="alter-asymmetric-key-transact-sql"></a>ALTER ASYMMETRIC KEY (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Изменяет свойства асимметричного ключа.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
ALTER ASYMMETRIC KEY Asym_Key_Name <alter_option>  
  
<alter_option> ::=  
      <password_change_option>   
    | REMOVE PRIVATE KEY   

<password_change_option> ::=  
    WITH PRIVATE KEY ( <password_option> [ , <password_option> ] )  

<password_option> ::=  
      ENCRYPTION BY PASSWORD = 'strongPassword'  
    | DECRYPTION BY PASSWORD = 'oldPassword'  
```  
  
## <a name="arguments"></a>Аргументы  
 *Asym_Key_Name*  
 Имя, под которым асимметричный ключ известен базе данных.  
  
 REMOVE PRIVATE KEY  
 Удаляет закрытый ключ из асимметричного ключа. Открытый ключ не удаляется.  
  
 WITH PRIVATE KEY  
 Изменяет защиту закрытого ключа.  
  
 ENCRYPTION BY PASSWORD **= "***stongPassword***"**  
 Указывает новый пароль для защиты закрытого ключа. *пароль* должен соответствовать требованиям политики паролей Windows компьютера, на котором выполняется экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Если этот аргумент не указан, закрытый ключ будет зашифрован с помощью главного ключа базы данных.  
  
 ПАРОЛЬ дешифрования УКАЗЫВАТЬ **= "***Старый_пароль***"**  
 Указывает старый пароль, которым в данный момент защищен закрытый ключ. Этот аргумент не требуется, если закрытый ключ защищается главным ключом базы данных.  
  
## <a name="remarks"></a>Замечания  
 Если главного ключа базы данных не существует, необходимо указать параметр ENCRYPTION BY PASSWORD, а если пароль не указан, операция завершится неуспешно. Сведения о том, как создать главный ключ базы данных см. в разделе [CREATE MASTER KEY &#40; Transact-SQL &#41; ](../../t-sql/statements/create-master-key-transact-sql.md).  
  
 Инструкция ALTER ASYMMETRIC KEY позволяет изменить защиту закрытого ключа с помощью параметров PRIVATE KEY так, как показано в следующей таблице.  
  
|Тип изменения защиты|ENCRYPTION BY PASSWORD|DECRYPTION BY PASSWORD|  
|----------------------------|----------------------------|----------------------------|  
|Изменение старого пароля на новый|Обязательно|Обязательное|  
|Изменение защиты паролем на защиту главным ключом|Пропустить|Обязательное|  
|Изменение защиты главным ключом на защиту паролем|Обязательное|Пропустить|  
  
 Чтобы главный ключ базы данных мог использоваться для защиты закрытого ключа, он сначала должен быть открыт. Дополнительные сведения см. в разделе [OPEN MASTER KEY &#40; Transact-SQL &#41; ](../../t-sql/statements/open-master-key-transact-sql.md).  
  
 Для изменения владельца асимметричного ключа, используйте [ALTER AUTHORIZATION](../../t-sql/statements/alter-authorization-transact-sql.md).  
  
## <a name="permissions"></a>Permissions  
 При удалении закрытого ключа необходимо иметь разрешение CONTROL на асимметричный ключ.  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-changing-the-password-of-the-private-key"></a>A. Изменение пароля закрытого ключа  
 В следующем примере изменяется пароль, используемый для защиты закрытого ключа асимметричного ключа `PacificSales09`. Новым паролем будет `<enterStrongPasswordHere>`.  
  
```  
ALTER ASYMMETRIC KEY PacificSales09   
    WITH PRIVATE KEY (  
    DECRYPTION BY PASSWORD = '<oldPassword>',  
    ENCRYPTION BY PASSWORD = '<enterStrongPasswordHere>');  
GO  
```  
  
### <a name="b-removing-the-private-key-from-an-asymmetric-key"></a>Б. Удаление закрытого ключа из асимметричного ключа  
 В следующем примере закрытый ключ удаляется из ассиметричного ключа `PacificSales19`, в котором остается только открытый ключ.  
  
```  
ALTER ASYMMETRIC KEY PacificSales19 REMOVE PRIVATE KEY;  
GO  
```  
  
### <a name="c-removing-password-protection-from-a-private-key"></a>В. Снятие парольной защиты с закрытого ключа  
 В следующем примере снимается парольная защита закрытого ключа и устанавливается его защита главным ключом базы данных.  
  
```  
OPEN MASTER KEY;  
ALTER ASYMMETRIC KEY PacificSales09 WITH PRIVATE KEY (  
    DECRYPTION BY PASSWORD = '<enterStrongPasswordHere>' );  
GO  
```  
  
## <a name="see-also"></a>См. также:  
 [CREATE ASYMMETRIC KEY &#40;Transact-SQL&#41;](../../t-sql/statements/create-asymmetric-key-transact-sql.md)   
 [DROP ASYMMETRIC KEY (Transact-SQL)](../../t-sql/statements/drop-asymmetric-key-transact-sql.md)   
 [Ключи шифрования базы данных и SQL Server (компонент Database Engine)](../../relational-databases/security/encryption/sql-server-and-database-encryption-keys-database-engine.md)   
 [Иерархия средств шифрования](../../relational-databases/security/encryption/encryption-hierarchy.md)   
 [CREATE MASTER KEY (Transact-SQL)](../../t-sql/statements/create-master-key-transact-sql.md)   
 [ОТКРЫТЬ ГЛАВНЫЙ ключ &#40; Transact-SQL &#41;](../../t-sql/statements/open-master-key-transact-sql.md)   
 [Расширенное управление ключами &#40;EKM&#41;](../../relational-databases/security/encryption/extensible-key-management-ekm.md)  
  
  

