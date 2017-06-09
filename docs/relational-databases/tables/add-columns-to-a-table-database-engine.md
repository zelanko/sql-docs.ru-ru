---
title: "Добавление столбцов в таблицу (ядро СУБД) | Документация Майкрософт"
ms.custom: 
ms.date: 10/27/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- dbe-tables
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- inserting columns
- columns [SQL Server], adding
- adding columns
ms.assetid: abeb8d52-d562-4e29-9e1e-2923ae874859
caps.latest.revision: 20
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: bc2034ac69dee1a72429e94841aec1763703de7c
ms.openlocfilehash: 82d9586bdd3dce6f463f9c142b4e0a1e9ddb3a72
ms.contentlocale: ru-ru
ms.lasthandoff: 06/05/2017

---
# <a name="add-columns-to-a-table-database-engine"></a>Добавление столбцов в таблицу (компонент Database Engine)
[!INCLUDE[tsql-appliesto-ss2016-all_md](../../includes/tsql-appliesto-ss2016-all-md.md)]

 > Материалы по предыдущим версиям SQL Server см. в разделе [Добавление столбцов в таблицу (ядро СУБД)](https://msdn.microsoft.com/en-US/library/ms190238(SQL.120).aspx).


  В данном разделе содержатся инструкции по добавлению новых столбцов в таблицу в [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] при помощи [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] или [!INCLUDE[tsql](../../includes/tsql-md.md)].  

  ##  <a name="BeforeYouBegin"></a> Перед началом  
  
###  <a name="Restrictions"></a> Ограничения  
 Использование инструкции ALTER TABLE для добавления столбцов в таблицу приводит к автоматическому добавлению этих столбцов в конец таблицы. Если требуется, чтобы столбцы располагались в таблице в определенном порядке, воспользуйтесь [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]. Однако помните, что это не рекомендуемый метод конструирования баз данных. Рекомендуется указывать порядок, в котором возвращаются столбцы, на уровне приложения и запроса. Не следует предполагать, что SELECT * будет возвращать все столбцы в ожидаемом порядке, основанном на порядке их определения в таблице. Всегда указывайте столбцы в запросах и приложениях по именам в том порядке, в котором они должны следовать.  
  
###  <a name="Security"></a> Безопасность  
  
####  <a name="Permissions"></a> Разрешения  
 Требуется разрешение ALTER на таблицу.  
  
##  <a name="SSMSProcedure"></a> Использование среды SQL Server Management Studio  
  
#### <a name="to-insert-columns-into-a-table-with-table-designer"></a>Вставка в таблицу столбцов с помощью конструктора таблиц  
  
1.  В **обозревателе объектов**щелкните правой кнопкой мыши таблицу, в которую необходимо добавить столбцы, и выберите пункт **Конструктор**.  
  
2.  Щелкните первую пустую ячейку в столбце **Имя столбца** .  
  
3.  Введите имя столбца в ячейку. Имя столбца — значение, которое необходимо указать.  
  
4.  Нажмите клавишу TAB, чтобы перейти к ячейке **Тип данных** и выбрать тип данных из раскрывающегося списка. Это — обязательное значение, и если его не указать, будет использоваться значение по умолчанию.  
  
    > [!NOTE]  
    >  Значения по умолчанию можно установить или изменить в диалоговом окне **Параметры** в разделе **Инструменты для баз данных**.  
  
5.  Продолжайте определение других свойств столбца во вкладке **Свойства столбца** .  
  
    > [!NOTE]  
    >  При создании нового столбца для свойств столбца устанавливаются значения по умолчанию, но их можно изменить на вкладке **Свойства столбца** .  
  
6.  По окончании добавления столбцов из меню **Файл** выберите пункт **Сохранить***имя таблицы*.  
  
##  <a name="TsqlProcedure"></a> Использование Transact-SQL  
  
#### <a name="to-insert-columns-into-a-table"></a>Вставка столбцов в таблицу  
  
1.  Установите соединение с компонентом [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  На панели «Стандартная» нажмите **Создать запрос**.  
  
3.  В следующем примере добавляются два столбца в таблицу `dbo.doc_exa`. Скопируйте следующий пример в окно запроса и нажмите кнопку **Выполнить**.  
  
```  
ALTER TABLE dbo.doc_exa ADD column_b VARCHAR(20) NULL, column_c INT NULL ;  
```  
  
####  <a name="FollowUp"></a>Дополнительные сведения см. в разделе [ALTER TABLE (Transact-SQL)](../../t-sql/statements/alter-table-transact-sql.md).  
  
  

