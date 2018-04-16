---
title: APP_NAME (Transact-SQL) | Документы Майкрософт
ms.custom: ''
ms.date: 07/24/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: ''
ms.component: t-sql|functions
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
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
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: aaea21b68fe0e7a9b0e57bf18d9e9907371dc9b6
ms.sourcegitcommit: 9351e8b7b68f599a95fb8e76930ab886db737e5f
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2018
---
# <a name="appname-transact-sql"></a>APP_NAME (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

Функция, возвращающая имя приложения для текущего сеанса, если оно задано приложением.
  
> [!IMPORTANT]  
>  Имя приложения указывается клиентом и не проверяется. Не используйте **APP_NAME** как часть проверки безопасности.  
  
![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>Синтаксис  
  
```sql
  
APP_NAME  ( )  
```  
  
## <a name="return-types"></a>Типы возвращаемых данных  
**nvarchar(128)**
  
## <a name="remarks"></a>Remarks  
Используйте **APP_NAME**, чтобы различать приложения, когда нужно выполнить разные действия для разных приложений. Например, с помощью **APP_NAME** можно различить приложения, чтобы использовать разный формат даты для каждого из них. Эта функция также позволяет возвратить информационное сообщение для некоторых приложений.
  
Чтобы задать имя приложения в [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)], щелкните элемент **Параметры** в диалоговом окне **Подключение к ядру СУБД**. На вкладке **Дополнительные параметры подключения** укажите атрибут **app** в формате `;app='application_name'`.
  
## <a name="example"></a>Пример  
Этот пример проверяет, является ли клиентское приложение, инициировавшее процесс, сеансом `SQL Server Management Studio` и предоставляет ли оно дату в формате US или ANSI.
  
```sql
USE AdventureWorks2012;  
GO  
IF APP_NAME() = 'Microsoft SQL Server Management Studio - Query'  
PRINT 'This process was started by ' + APP_NAME() + '. The date is ' + CONVERT ( varchar(100) , GETDATE(), 101) + '.';  
ELSE   
PRINT 'This process was started by ' + APP_NAME() + '. The date is ' + CONVERT ( varchar(100) , GETDATE(), 102) + '.';  
GO  
```  
  
## <a name="see-also"></a>См. также раздел
[Системные функции (Transact-SQL)](../../relational-databases/system-functions/system-functions-for-transact-sql.md)  
[Функции](../../t-sql/functions/functions.md)
  
  
