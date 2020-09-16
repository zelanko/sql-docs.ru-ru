---
description: Создание синонимов
title: Создание синонимов | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.technology: t-sql
ms.topic: conceptual
f1_keywords:
- sql13.swb.synonym.general.f1
helpviewer_keywords:
- creating synonyms
- synonyms [SQL Server], creating
ms.assetid: fedfa7a5-d0b6-4e2b-90f4-a08122958e33
author: markingmyname
ms.author: maghan
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: f5c4d25ed48715c9317ebe0df37ee4d2779abe10
ms.sourcegitcommit: dd36d1cbe32cd5a65c6638e8f252b0bd8145e165
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/08/2020
ms.locfileid: "89551604"
---
# <a name="create-synonyms"></a>Создание синонимов
[!INCLUDE [SQL Server Azure SQL Database](../../includes/applies-to-version/sql-asdb.md)]
  В этом разделе описывается создание синонима в [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] с помощью [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] или [!INCLUDE[tsql](../../includes/tsql-md.md)].  
  
 **В этом разделе**  
  
-   **Перед началом работы**  
  
     [Безопасность](#Security)  
  
-   **Создание синонима при помощи:**  
  
     [Среда SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> Перед началом  
  
###  <a name="security"></a><a name="Security"></a> безопасность  
 Для создания синонима в заданной схеме пользователь должен иметь разрешение CREATE SYNONYM и, либо владеть схемой, либо иметь разрешение ALTER SCHEMA. Разрешение на выполнение CREATE SYNONYM можно предоставлять.  
  
####  <a name="permissions"></a><a name="Permissions"></a> Permissions  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> Использование среды SQL Server Management Studio  
  
#### <a name="to-create-a-synonym"></a>Создание синонима  
  
1.  В **обозревателе объектов**разверните базу данных, в которой необходимо создать новое представление.  
  
2.  Щелкните правой кнопкой мыши папку **Синонимы** и выберите **Создать синоним...**  
  
3.  В диалоговом окне **Добавление синонима** введите следующие сведения.  

     **Имя синонима**  
     Введите новое имя, которое будет использоваться для обращения к этому объекту.  
  
     **Схема синонима**  
     Введите схему нового имени, которая будет использоваться для обращения к этому объекту.  
  
     **Имя сервера**  
     Введите экземпляр сервера для подключения.  
  
     **Имя базы данных**  
     Введите или выберите базу данных, содержащую объект.  
  
     **Схема**  
     Введите или выберите схему, владеющую объектом.  
  
     **Тип объекта**  
     Выберите тип объекта.  
  
     **Имя объекта**  
     Введите имя объекта, которому должен соответствовать синоним.  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> Использование Transact-SQL  
  
#### <a name="to-create-a-synonym"></a>Создание синонима  
  
1.  Установите соединение с компонентом [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  На панели «Стандартная» нажмите **Создать запрос**.  
  
3.  Скопируйте следующие примеры в окно запроса и нажмите кнопку **Выполнить**.  
  
###  <a name="example-transact-sql"></a><a name="TsqlExample"></a> Примеры (Transact-SQL)  
 В следующем примере создается синоним для существующей таблицы в базе данных [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] . Затем синоним используется в последующих примерах.  
  
```  
USE tempdb;  
GO  
CREATE SYNONYM MyAddressType  
FOR AdventureWorks2012.Person.AddressType;  
GO  
```  
  
 Следующий пример вставляет строку в базовую таблицу, на которую ссылается синоним `MyAddressType` .  
  
```  
USE tempdb;  
GO  
INSERT INTO MyAddressType (Name)  
VALUES ('Test');  
GO  
```  
  
 Следующий пример демонстрирует, как на синоним можно сослаться в динамическом SQL.  
  
```  
USE tempdb;  
GO  
EXECUTE ('SELECT Name FROM MyAddressType');  
GO  
```  
  
  
