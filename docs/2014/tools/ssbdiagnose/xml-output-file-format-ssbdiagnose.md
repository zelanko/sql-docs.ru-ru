---
title: Формат выходного XML-файла (ssbdiagnose) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: tools-other
ms.topic: conceptual
helpviewer_keywords:
- XML output file format [ssbdiagnose]
- ssbdiagnose
ms.assetid: 3ceb991b-6f15-4504-8828-de5adf448bc5
author: stevestein
ms.author: sstein
ms.openlocfilehash: 56758f15a3bd2a71221c936a80f7455d9e1c1cd9
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/18/2020
ms.locfileid: "85057621"
---
# <a name="xml-output-file-format-ssbdiagnose"></a>Формат выходного XML-файла (программа ssbdiagnose)
  Если запустить программу **ssbdiagnose** с параметром **-XML** , то выходные данные будут выданы в виде XML-файла. В выходном XML-файле содержатся заголовок и ошибки, обнаруженные в результате анализа конфигурации компонента [!INCLUDE[ssSB](../../includes/sssb-md.md)] или диалога. Для анализа ошибок, перечисленных в файле, и создания отчета по ним можно написать пользовательское приложение. Кроме того, XML-файл можно просмотреть в стандартном XML-редакторе, например в XML-блокноте.  
  
 Выходной файл программы **ssbdiangose** содержит корневой элемент DiagnosticInformation с двумя дочерними типами:  
  
-   элемент Banner с данными заголовка;  
  
-   элемент Issue для каждой проблемы, обнаруженной программой **ssbdiagnose**.  
  
## <a name="diagnosticinformation-root-element"></a>Корневой элемент DiagnosticInformation  
  
-   [Элемент DiagnosticInformation (программа ssbdiagnose)](diagnosticinformation-element-ssbdiagnose.md)  
  
## <a name="banner-element"></a>Элемент Banner  
  
-   [Элемент Banner (программа ssbdiagnose)](banner-element-ssbdiagnose.md)  
  
## <a name="issue-element"></a>Элемент Issue  
  
-   [Элемент Issue (программа ssbdiagnose)](issue-element-ssbdiagnose.md)  
  
## <a name="see-also"></a>См. также:  
 [Программа ssbdiagnose (компонент Service Broker)](ssbdiagnose-utility-service-broker.md)  
  
  
