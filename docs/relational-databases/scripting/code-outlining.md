---
title: "Структурирование кода | Документация Майкрософт"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-non-specified
ms.prod_service: ssms
ms.service: 
ms.component: scripting
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Query Editor [SQL Server Management Studio], outlining code
- Query Editor [SQL Server Management Studio], hiding code
ms.assetid: 556c7dfe-7bc8-4cab-a36f-2b753a05d3f1
caps.latest.revision: "14"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: f45444823bfc10a1c756ecc0efa2dd1683536c3c
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="code-outlining"></a>Структурирование кода
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)] Функция структурирования в редакторах запросов среды [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] позволяет выборочно скрывать части кода при редактировании запросов. Это делает просмотр кода при редактировании более удобным, особенно когда файл запроса имеет большой размер.  
  
## <a name="outlining-overview"></a>Общие сведения о функции структурирования  
 По умолчанию при открытии окна редактора запросов весь код является видимым. Участки кода можно свернуть, чтобы скрыть их. Квадрат со знаком «минус» (-) возле вертикальной линии, проходящей вдоль левого края окна редактора, обозначает начало каждого сворачиваемого участка кода. Если щелкнуть значок «минус», то текст участка кода будет заменен полем, содержащим три точки (…), а значок «минус» заменяется значком «плюс» (+). Если щелкнуть значок «плюс», то свернутый код будет отображен, а значок «плюс» заменен значком «минус». Если указатель находится над полем с тремя точками, то отображается всплывающая подсказка, содержащая код свернутого раздела.  
  
## <a name="system-outline-regions"></a>Системные структурные области  
 Каждый редактор в среде [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] формирует набор структурных областей, по умолчанию определяемых системой.  
  
 Редакторы кода многомерных выражений и расширений интеллектуального анализа данных создают структурные области для каждой многострочной инструкции. Это единственный уровень структурирования, поддерживаемый этими редакторами.  
  
### <a name="analysis-services-xmla-query-editor-regions"></a>Области редактора запросов XMLA служб Analysis Services  
 Редактор запросов XMLA служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] формирует структурную область для каждого многострочного XML-атрибута. Редактор создает вложенные структурные области для вложенных тегов. Например, редактор XMLA создает три структурные области в следующем документе.  
  
 ![XML-код, демонстрирующий структурирование](../../relational-databases/scripting/media/editoutlinexmlfull.gif "XML-код, демонстрирующий структурирование")  
  
 Если щелкнуть значок "минус" в строке \<InnerTag>, то будет свернут только InnerTag, как показано на следующей иллюстрации.  
  
 ![XML-код со скрытым внутренним узлом](../../relational-databases/scripting/media/editoutlinexmlinnercol.gif "XML-код со скрытым внутренним узлом")  
  
 Когда указатель находится над полем с тремя точками (...), то код в свернутой области отображается во всплывающей подсказке, как показано на следующей иллюстрации.  
  
 ![XML-код с подсказками, отображающими скрытый код](../../relational-databases/scripting/media/editoutlinexmlmouse.gif "XML-код с подсказками, отображающими скрытый код")  
  
 Если щелкнуть значок "минус" в строке \<MiddleTag>, то будут свернуты и MiddleTag, и InnerTag, как показано на следующей иллюстрации.  
  
 ![XML-код со скрытыми внутренним и средним тегами](../../relational-databases/scripting/media/editoutlinexmlmiddlecol.gif "XML-код со скрытыми внутренним и средним тегами")  
  
 Если щелкнуть значок "минус" в строке \<OuterTag>, то будут свернуты все три строки, как показано на следующей иллюстрации.  
  
 ![XML-код с тремя скрытыми тегами](../../relational-databases/scripting/media/editoutlinexmloutercol.gif "XML-код с тремя скрытыми тегами")  
  
### <a name="database-engine-query-editor-regions"></a>Области редактора запросов к ядру СУБД  
 Редактор запросов компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)] формирует структурные области для каждого элемента в следующей иерархии.  
  
1.  Пакеты. Первый пакет содержит код от начала файла до первой команды GO либо до конца файла, если он не содержит команд GO. Каждый последующий пакет после первой команды GO охватывает код от соответствующей команды GO до следующей команды GO, либо до конца файла.  
  
2.  Блоки, разделяемые следующими ключевыми словами:  
  
    -   BEGIN — END  
  
    -   BEGIN TRY — END TRY  
  
    -   BEGIN CATCH — END CATCH  
  
3.  Многострочные инструкции.  
  
 Например, редактор запросов компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)] создает три структурные области в следующем запросе.  
  
```  
CREATE PROCEDURE Sales.SampleProc --Outline region 1  
AS  
BEGIN --Outline region 2   
  SELECT GETDATE() AS TimeOfQuery;  
  SELECT * --Outline region 3  
  FROM sys.transmission_queue;  
  SELECT @@VERSION;  
END;  
GO  
```  
  
 Щелкнув значок «минус» в строке `SELECT *` , можно свернуть только инструкцию `SELECT` . Чтобы свернуть весь блок `BEGIN - END` , щелкните значок «минус» в строке `BEGIN` . Чтобы свернуть весь блок `GO` , щелкните значок «минус» в строке `CREATE PROCEDURE` . Свернуть строки `SELECT GETDATE()` или `SELECT @@VERSION` по отдельности нельзя, поскольку они являются однострочными инструкциями и не выделяются в структурные области.  
  
  
