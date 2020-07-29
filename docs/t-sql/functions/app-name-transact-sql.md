---
title: APP_NAME (Transact-SQL) | Документы Майкрософт
ms.custom: ''
ms.date: 07/24/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
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
author: markingmyname
ms.author: maghan
ms.openlocfilehash: 5bba743ec083c5eda630e9d14799cae34726a848
ms.sourcegitcommit: 768f046107642f72693514f51bf2cbd00f58f58a
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/23/2020
ms.locfileid: "87113198"
---
# <a name="app_name-transact-sql"></a>APP_NAME (Transact-SQL)
[!INCLUDE [SQL Server SQL Database](../../includes/applies-to-version/sql-asdb.md)]

Эта функция возвращает имя приложения для текущего сеанса, если оно задано приложением.
  
> [!IMPORTANT]  
>  Имя приложения указывается клиентом и `APP_NAME` никак не проверяет его значение. Не используйте `APP_NAME` как часть проверки безопасности.  
  
![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>Синтаксис  
  
```sql
  
APP_NAME  ( )  
```  
  
[!INCLUDE[sql-server-tsql-previous-offline-documentation](../../includes/sql-server-tsql-previous-offline-documentation.md)]

## <a name="return-types"></a>Типы возвращаемых данных
**nvarchar(128)**
  
## <a name="remarks"></a>Remarks  
Используйте `APP_NAME`, чтобы различать приложения, когда нужно выполнить разные действия для разных приложений. Например, с помощью `APP_NAME` можно различить приложения, чтобы использовать разный формат даты для каждого из них. Эта функция также позволяет возвратить информационное сообщение для некоторых приложений.
  
Чтобы задать имя приложения в [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)], щелкните элемент **Параметры** в диалоговом окне **Подключение к ядру СУБД**. На вкладке **Дополнительные параметры подключения** укажите атрибут **app** в формате `;app='application_name'`.
  
## <a name="example"></a>Пример  
В следующем примере проверяется, является ли клиентское приложение, запустившее процесс, сеансом среды `SQL Server Management Studio`. Затем значение даты предоставляется в формате US или ANSI.
  
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
[Системные функции (Transact-SQL)](../../relational-databases/system-functions/system-functions-category-transact-sql.md)  
[Функции](../../t-sql/functions/functions.md)
  
  
