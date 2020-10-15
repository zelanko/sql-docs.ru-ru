---
title: Использование объектов SQL Server 2012 в своем проекте
description: Ознакомьтесь с последовательностями в SQL Server 2012. Узнайте, как добавлять эти объекты в проекты баз данных и использовать их в запросах.
ms.prod: sql
ms.technology: ssdt
ms.topic: conceptual
ms.assetid: 9baf122f-cf22-4860-98db-ef782cd972fc
author: markingmyname
ms.author: maghan
ms.reviewer: “”
ms.custom: seo-lt-2019
ms.date: 02/09/2017
ms.openlocfilehash: ee09f89463151f0dcf5c1fcd2c1f82a72ba8f350
ms.sourcegitcommit: a41e1f4199785a2b8019a419a1f3dcdc15571044
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/13/2020
ms.locfileid: "91988190"
---
# <a name="how-to-use-microsoft-sql-server-2012-objects-in-your-project"></a>Руководство. использовать объекты Microsoft SQL Server 2012 в своем проекте

В этом примере мы добавим в проект базы данных объект последовательности, ориентированный на Microsoft SQL Server 2012.  
  
Последовательности добавляются в Microsoft SQL Server 2012. Последовательность представляет собой определяемый пользователем объект, привязанный к схеме, который формирует последовательность числовых значений в соответствии со спецификацией, с которой эта последовательность создавалась. Последовательность числовых значений формируется в возрастающем или убывающем порядке с определенным интервалом и может повторяться запрошенным образом.  Дополнительные сведения об объектах последовательности см. в статье [Sequence Numbers](../relational-databases/sequence-numbers/sequence-numbers.md) (Порядковые номера). Дополнительные сведения о новых возможностях в Microsoft SQL Server 2012 см. в разделе [Новые возможности SQL Server 2012](/previous-versions/sql/sql-server-2012/bb500435(v=sql.110)).  
  
> [!WARNING]  
> В следующих процедурах используются сущности, созданные с помощью процедур, которые описывались ранее в разделах [Connected Database Development](../ssdt/connected-database-development.md) (Разработка подключенной базы данных) и [Project-Oriented Offline Database Development](../ssdt/project-oriented-offline-database-development.md) (Разработка базы данных вне сети с учетом проекта).  
  
### <a name="to-add-a-new-sequence-object-to-your-project"></a>Добавление нового объекта последовательности в проект  
  
1.  Щелкните правой кнопкой мыши проект базы данных **TradeDev** в **обозревателе решений**, а затем последовательно выберите **Добавить** и **Создать элемент**.  
  
2.  В области слева щелкните **Программирование** и выберите **Последовательность**. Щелкните **Добавить**, чтобы добавить новый объект в проект.  
  
3.  Замените код по умолчанию приведенным ниже:  
  
    ```  
    CREATE SEQUENCE [dbo].[Seq1]  
    AS INT  
    START WITH 1  
    INCREMENT BY 1  
    MAXVALUE 1000  
    NO CYCLE  
    CACHE 10  
    ```  
  
4.  Если для целевой платформы проекта вместо Microsoft SQL Server 2012 указано другое значение, то в **Списке ошибок** отобразится сообщение о синтаксической ошибке для инструкции `CREATE SEQUENCE`. Чтобы исправить эту ошибку, см. раздел [Руководство. Изменение целевой платформы и публикация проекта базы данных](../ssdt/how-to-change-target-platform-and-publish-a-database-project.md); здесь рассказывается, как изменить целевую платформу соответствующим образом.  
  
5.  Следуйте инструкциям в статье [Как изменить целевую платформу и опубликовать проект базы данных](../ssdt/how-to-change-target-platform-and-publish-a-database-project.md), чтобы опубликовать проект в базе данных на подключенном сервере Microsoft SQL Server 2012.  
  
### <a name="to-use-the-new-sequence-object"></a>Использование нового объекта последовательности  
  
1.  В окне обозревателя объектов SQL Server правой кнопкой мыши щелкните базу данных, опубликованную в рамках описанной ранее процедуры, и выберите команду **Создать запрос**.  
  
2.  Вставьте следующий код в окно запроса.  
  
    ```  
    DECLARE @counter INT  
    SET @counter=0  
    WHILE @counter<10  
    BEGIN  
        SET @counter = @counter +1  
         INSERT dbo.Products (Id, Name, CustomerId) VALUES (NEXT VALUE FOR dbo.Seq1, 'ProductItem'+cast(@counter as varchar), 1)  
    END   
    GO  
    ```  
  
3.  Нажмите кнопку **Выполнить запрос**.  
  
4.  В окне **обозревателя объектов SQL Server** перейдите к таблице **Products** в базе данных. Щелкните правой кнопкой мыши и выберите пункт **Просмотр данных**, чтобы просмотреть добавленные строки.  
