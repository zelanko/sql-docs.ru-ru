---
title: Создание главного ключа базы данных | Документация Майкрософт
ms.custom: ''
ms.date: 09/12/2019
ms.prod: sql-server-2014
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- database master key [SQL Server], creating
ms.assetid: 8cb24263-e97d-4e4d-9429-6cf494a4d5eb
author: jaszymas
ms.author: jaszymas
ms.reviewer: carlrab
ms.openlocfilehash: cb8305d9d5a3c72e6dffafd231f21110a5abdd14
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/18/2020
ms.locfileid: "85055341"
---
# <a name="create-a-database-master-key"></a>Создание главного ключа базы данных

В этом разделе описывается создание главного ключа базы данных в `master` базе данных в [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] с помощью [!INCLUDE[tsql](../../../includes/tsql-md.md)] .

**В этом разделе**

- **Перед началом работы**

  [Безопасность](#Security)

- [Создание главного ключа базы данных с помощью Transact-SQL](#TsqlProcedure)

## <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> Перед началом

### <a name="security"></a><a name="Security"></a> безопасность

#### <a name="permissions"></a><a name="Permissions"></a> Permissions

Требует разрешения CONTROL для базы данных.

## <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> Использование Transact-SQL

### <a name="to-create-a-database-master-key"></a>Создание главного ключа базы данных

1. Выберите пароль для шифрования копии главного ключа базы данных, которая будет храниться в базе данных.
2. В **обозревателе объектов**подключитесь к экземпляру компонента [!INCLUDE[ssDE](../../../includes/ssde-md.md)].
3. Разверните узел **Системные базы данных**, щелкните правой кнопкой мыши базу данных `master` и выберите пункт **Создать запрос**.
4. Скопируйте следующий пример в окно запроса и нажмите кнопку **Выполнить**.

  ```sql
  -- Creates the master key.
  -- The key is encrypted using the password "23987hxJ#KL95234nl0zBe."
  CREATE MASTER KEY ENCRYPTION BY PASSWORD = '23987hxJ#KL95234nl0zBe';
```

Дополнительные сведения см. в разделе [CREATE MASTER KEY (Transact-SQL)](/sql/t-sql/statements/create-master-key-transact-sql).
