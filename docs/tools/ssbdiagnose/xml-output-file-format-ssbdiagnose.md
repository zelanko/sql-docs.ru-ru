---
title: Формат выходного файла XML (ssbdiagnose) | Документация Майкрософт
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
helpviewer_keywords:
- XML output file format [ssbdiagnose]
- ssbdiagnose
ms.assetid: 3ceb991b-6f15-4504-8828-de5adf448bc5
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 35efa723a022ca4982b5d7113041841b508cf7d3
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47815122"
---
# <a name="xml-output-file-format-ssbdiagnose"></a>Формат выходного XML-файла (программа ssbdiagnose)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Если запустить программу **ssbdiagnose** с параметром **-XML**, то выходные данные будут выданы в виде XML-файла. В выходном XML-файле содержатся заголовок и ошибки, обнаруженные в результате анализа конфигурации компонента [!INCLUDE[ssSB](../../includes/sssb-md.md)] или диалога. Для анализа ошибок, перечисленных в файле, и создания отчета по ним можно написать пользовательское приложение. Кроме того, XML-файл можно просмотреть в стандартном XML-редакторе, например в XML-блокноте.  
  
 Выходной файл программы **ssbdiangose** содержит корневой элемент DiagnosticInformation с двумя дочерними типами:  
  
-   элемент Banner с данными заголовка;  
  
-   элемент Issue для каждой проблемы, обнаруженной программой **ssbdiagnose**.  
  
## <a name="diagnosticinformation-root-element"></a>Корневой элемент DiagnosticInformation  
  
-   [Элемент DiagnosticInformation (программа ssbdiagnose)](../../tools/ssbdiagnose/diagnosticinformation-element-ssbdiagnose.md)  
  
## <a name="banner-element"></a>Элемент Banner  
  
-   [Элемент Banner (программа ssbdiagnose)](../../tools/ssbdiagnose/banner-element-ssbdiagnose.md)  
  
## <a name="issue-element"></a>Элемент Issue  
  
-   [Элемент Issue (программа ssbdiagnose)](../../tools/ssbdiagnose/issue-element-ssbdiagnose.md)  
  
## <a name="see-also"></a>См. также:  
 [Программа ssbdiagnose (компонент Service Broker)](../../tools/ssbdiagnose/ssbdiagnose-utility-service-broker.md)  
  
  
