---
title: "APP_NAME (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 07/24/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- APP_NAME_TSQL
- APP_NAME
dev_langs:
- TSQL
helpviewer_keywords:
- name checking for current session [SQL Server]
- sessions [SQL Server], application names
- applications [SQL Server], names
- current session application names
- APP_NAME function
ms.assetid: e491e192-9b30-4243-bc19-33c133fe08a8
caps.latest.revision: 35
author: edmacauley
ms.author: edmaca
manager: cguyer
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: c4f63ae216bad0269415ac5e0aa57a7543500f0c
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="appname-transact-sql"></a>APP_NAME (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

Возвращает имя приложения для текущего сеанса, если оно установлено приложением. 
  
> [!IMPORTANT]  
>  Имя приложения указывается клиентом и не проверяется. Не используйте **APP_NAME** как часть проверки безопасности.  
  
![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>Синтаксис  
  
```sql
  
APP_NAME  ( )  
```  
  
## <a name="return-types"></a>Типы возвращаемых значений  
**nvarchar(128)**
  
## <a name="remarks"></a>Замечания  
Используйте **APP_NAME** при необходимости выполнять различные действия для различных приложений. Например, разное форматирование даты для разных приложений или возвращение информационного сообщения в определенные приложения.
  
Чтобы задать имя приложения в [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]в **подключиться к компоненту Database Engine** диалоговое окно, нажмите кнопку **параметры**. На **Дополнительные параметры соединения** укажите **приложения** атрибута в формате`;app='application_name'`
  
## <a name="examples"></a>Примеры  
В следующем примере проверяется, является ли клиентское приложение, инициировавшее процесс, сеансом `SQL Server Management Studio` и предоставляет ли оно дату в формате US или ANSI.
  
```sql
USE AdventureWorks2012;  
GO  
IF APP_NAME() = 'Microsoft SQL Server Management Studio - Query'  
PRINT 'This process was started by ' + APP_NAME() + '. The date is ' + CONVERT ( varchar(100) , GETDATE(), 101) + '.';  
ELSE   
PRINT 'This process was started by ' + APP_NAME() + '. The date is ' + CONVERT ( varchar(100) , GETDATE(), 102) + '.';  
GO  
```  
  
## <a name="see-also"></a>См. также:
[Системные функции &#40; Transact-SQL &#41;](../../relational-databases/system-functions/system-functions-for-transact-sql.md)  
[Функции](../../t-sql/functions/functions.md)
  
  

