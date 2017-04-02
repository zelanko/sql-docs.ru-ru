---
title: "Формат выходного XML-файла (программа ssbdiagnose) | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "формат выходного XML-файла [ssbdiagnose]"
  - "ssbdiagnose"
ms.assetid: 3ceb991b-6f15-4504-8828-de5adf448bc5
caps.latest.revision: 13
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 13
---
# Формат выходного XML-файла (программа ssbdiagnose)
  Если запустить программу **ssbdiagnose** с параметром **-XML**, то выходные данные будут выданы в виде XML-файла. В выходном XML-файле содержатся заголовок и ошибки, обнаруженные в результате анализа конфигурации компонента [!INCLUDE[ssSB](../../includes/sssb-md.md)] или диалога. Для анализа ошибок, перечисленных в файле, и создания отчета по ним можно написать пользовательское приложение. Кроме того, XML-файл можно просмотреть в стандартном XML-редакторе, например в XML-блокноте.  
  
 Выходной файл программы **ssbdiangose** содержит корневой элемент DiagnosticInformation с двумя дочерними типами:  
  
-   элемент Banner с данными заголовка;  
  
-   элемент Issue для каждой проблемы, обнаруженной программой **ssbdiagnose**.  
  
## Корневой элемент DiagnosticInformation  
  
-   [Элемент DiagnosticInformation (программа ssbdiagnose)](../../tools/ssbdiagnose/diagnosticinformation-element-ssbdiagnose.md)  
  
## Элемент Banner  
  
-   [Элемент Banner (программа ssbdiagnose)](../../tools/ssbdiagnose/banner-element-ssbdiagnose.md)  
  
## Элемент Issue  
  
-   [Элемент Issue (программа ssbdiagnose)](../../tools/ssbdiagnose/issue-element-ssbdiagnose.md)  
  
## См. также:  
 [Служебная программа ssbdiagnose (компонент Service Broker)](../../tools/ssbdiagnose/ssbdiagnose-utility-service-broker.md)  
  
  