---
description: Идентификатор SUSER_ID (Transact-SQL)
title: SUSER_ID (Transact-SQL) | Документы Майкрософт
ms.custom: ''
ms.date: 09/07/2018
ms.prod: sql
ms.prod_service: sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- SUSER_ID_TSQL
- SUSER_ID
dev_langs:
- TSQL
helpviewer_keywords:
- users [SQL Server], IDs
- logins [SQL Server], IDs
- SUSER_ID function
- IDs [SQL Server], logins
- identification numbers [SQL Server], logins
- user IDs [SQL Server]
ms.assetid: 348911ab-b0b6-4867-aee7-e6f42e053a4a
author: VanMSFT
ms.author: vanto
monikerRange: =azuresqldb-mi-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017
ms.openlocfilehash: 8a05992f921eadfc59e28cb21e3ada3594368b73
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88445560"
---
# <a name="suser_id-transact-sql"></a>Идентификатор SUSER_ID (Transact-SQL)
[!INCLUDE [SQL Server - ASDBMI](../../includes/applies-to-version/sql-asdbmi.md)]

  Возвращает идентификационный номер имени входа пользователя.  
  
> [!NOTE]  
>  Начиная с [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)], функция SUSER_ID возвращает значения, перечисленные в списке **principal_id** в представлении каталога **sys.server_principals**.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
SUSER_ID ( [ 'login' ] )   
```  
  
[!INCLUDE[sql-server-tsql-previous-offline-documentation](../../includes/sql-server-tsql-previous-offline-documentation.md)]

## <a name="arguments"></a>Аргументы
 **'** *login* **'**  
 Имя входа пользователя. Аргумент *login* имеет тип **nchar**. Если в качестве *login* указано значение типа **char**, *login* неявно преобразуется в тип **nchar**. *login* может быть любым именем входа [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], пользователем или группой Windows с разрешением на подключение к экземпляру [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Если аргумент *login* не задан, то возвращается идентификационный номер имени входа для текущего пользователя. Если параметр содержит слово NULL, то возвращается NULL.  
  
## <a name="return-types"></a>Типы возвращаемых данных  
 **int**  
  
## <a name="remarks"></a>Remarks  
 Функция SUSER_ID возвращает идентификационные номера только для тех имен входа, которые были явным образом описаны в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Этот идентификатор используется в рамках [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] для отслеживания прав собственности и разрешений. Данный идентификатор не является эквивалентом идентификационной записи системы безопасности (SID) для имени входа, возвращаемого функцией SUSER_SID. Если аргумент *login* является именем входа SQL Server, то значение SID сопоставляется с идентификатором GUID. Если аргумент *login* является именем входа Windows или группы Windows, то значение SID сопоставляется с идентификатором безопасности Windows.  
  
 Функция SUSER_SID возвращает SUID только для тех имен входа, для которых существуют записи в системной таблице **syslogins**.  
  
 Системные функции могут быть использованы в списке выбора, в предложении WHERE, и везде, где разрешено использование выражения, и за ними всегда должны следовать скобки, даже если не заданы никакие параметры.  
  
## <a name="examples"></a>Примеры  
 В следующем примере возвращается идентификационный номер для имени входа `sa`.  
  
```  
SELECT SUSER_ID('sa');  
```  
  
## <a name="see-also"></a>См. также:  
 [sys.server_principals (Transact-SQL)](../../relational-databases/system-catalog-views/sys-server-principals-transact-sql.md)   
 [SUSER_SID (Transact-SQL)](../../t-sql/functions/suser-sid-transact-sql.md)   
 [Системные функции (Transact-SQL)](../../relational-databases/system-functions/system-functions-category-transact-sql.md)  
  
  
