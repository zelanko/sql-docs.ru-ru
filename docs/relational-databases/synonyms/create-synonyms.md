---
title: "Создание синонимов | Документация Майкрософт"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: get-started-article
f1_keywords: sql13.swb.synonym.general.f1
helpviewer_keywords:
- creating synonyms
- synonyms [SQL Server], creating
ms.assetid: fedfa7a5-d0b6-4e2b-90f4-a08122958e33
caps.latest.revision: "7"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: 474f8498c3687a2fb377ed469c2f9381770521fa
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/09/2017
---
# <a name="create-synonyms"></a>Создание синонимов
  В этом разделе описывается создание синонима в [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] с помощью [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] или [!INCLUDE[tsql](../../includes/tsql-md.md)].  
  
 **В этом разделе**  
  
-   **Перед началом работы выполните следующие действия.**  
  
     [Безопасность](#Security)  
  
-   **Создание синонима при помощи:**  
  
     [Среда SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> Перед началом  
  
###  <a name="Security"></a> Безопасность  
 Для создания синонима в заданной схеме пользователь должен иметь разрешение CREATE SYNONYM и, либо владеть схемой, либо иметь разрешение ALTER SCHEMA. Разрешение на выполнение CREATE SYNONYM можно предоставлять.  
  
####  <a name="Permissions"></a> Разрешения  
  
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
  
###  <a name="TsqlExample"></a> Пример (Transact-SQL)  
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
  
  
