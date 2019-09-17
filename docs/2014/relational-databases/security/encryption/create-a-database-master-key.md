---
title: Создание главного ключа базы данных | Документация Майкрософт
ms.custom: ''
ms.date: 09/12/2019
ms.prod: sql-server-2014
ms.reviewer: carlrab
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- database master key [SQL Server], creating
ms.assetid: 8cb24263-e97d-4e4d-9429-6cf494a4d5eb
author: aliceku
ms.author: aliceku
manager: craigg
ms.openlocfilehash: 757b6c62d63da2b8f1fa33e5d704d7a2c4fabd38
ms.sourcegitcommit: 5a61854ddcd2c61bb6da30ccad68f0ad90da0c96
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/13/2019
ms.locfileid: "70978370"
---
# <a name="create-a-database-master-key"></a>Создание главного ключа базы данных

В этом разделе описывается создание главного ключа `master` базы данных в базе данных в [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] с помощью [!INCLUDE[tsql](../../../includes/tsql-md.md)].

**В этом разделе**

- **Перед началом работы**

  [безопасность](#Security)

- [Создание главного ключа базы данных с помощью Transact-SQL](#TsqlProcedure)

## <a name="BeforeYouBegin"></a> Перед началом

### <a name="Security"></a> безопасность

#### <a name="Permissions"></a> Permissions

Требует разрешения CONTROL для базы данных.

## <a name="TsqlProcedure"></a> Использование Transact-SQL

### <a name="to-create-a-database-master-key"></a>Создание главного ключа базы данных

1. Выберите пароль для шифрования копии главного ключа базы данных, которая будет храниться в базе данных.
2. В **обозревателе объектов**подключитесь к экземпляру компонента [!INCLUDE[ssDE](../../../includes/ssde-md.md)].
3. Разверните узел **системные базы данных**, щелкните `master` правой кнопкой мыши и выберите пункт **создать запрос**.
4. Скопируйте следующий пример в окно запроса и нажмите кнопку **Выполнить**.

  ```sql
  -- Creates the master key.
  -- The key is encrypted using the password "23987hxJ#KL95234nl0zBe."
  CREATE MASTER KEY ENCRYPTION BY PASSWORD = '23987hxJ#KL95234nl0zBe';
```

Дополнительные сведения см. в разделе [CREATE MASTER KEY (Transact-SQL)](/sql/t-sql/statements/create-master-key-transact-sql).
