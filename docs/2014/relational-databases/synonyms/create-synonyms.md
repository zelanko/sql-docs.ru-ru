---
title: Создание синонимов | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: t-sql
ms.topic: conceptual
f1_keywords:
- sql12.swb.synonym.general.f1
helpviewer_keywords:
- creating synonyms
- synonyms [SQL Server], creating
ms.assetid: fedfa7a5-d0b6-4e2b-90f4-a08122958e33
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: e2a45cf4f34b73996b6ecbd4f9cbb5f5a902e760
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "62854975"
---
# <a name="create-synonyms"></a>Создание синонимов
  В этом разделе описывается создание синонима в [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] с помощью [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] или [!INCLUDE[tsql](../../includes/tsql-md.md)].  
  
 **В этом разделе**  
  
-   **Перед началом работы**  
  
     [безопасность](#Security)  
  
-   **Создание синонима при помощи:**  
  
     [Среда SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> Перед началом  
  
###  <a name="Security"></a> безопасность  
 Для создания синонима в заданной схеме пользователь должен иметь разрешение CREATE SYNONYM и, либо владеть схемой, либо иметь разрешение ALTER SCHEMA. Разрешение на выполнение CREATE SYNONYM можно предоставлять.  
  
####  <a name="Permissions"></a> Permissions  
  
##  <a name="SSMSProcedure"></a> Использование среды SQL Server Management Studio  
  
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
  
##  <a name="TsqlProcedure"></a> Использование Transact-SQL  
  
#### <a name="to-create-a-synonym"></a>Создание синонима  
  
1.  Установите соединение с компонентом [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  На панели «Стандартная» нажмите **Создать запрос**.  
  
3.  Скопируйте следующие примеры в окно запроса и нажмите кнопку **Выполнить**.  
  
###  <a name="TsqlExample"></a> Примеры (Transact-SQL)  
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
  
  
