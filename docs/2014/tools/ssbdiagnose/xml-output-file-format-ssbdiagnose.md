---
title: Формат выходного файла XML (ssbdiagnose) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- XML output file format [ssbdiagnose]
- ssbdiagnose
ms.assetid: 3ceb991b-6f15-4504-8828-de5adf448bc5
caps.latest.revision: 12
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: fd4555fdcf53aace8eb48b74f0c62c7da9bf21e8
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37183481"
---
# <a name="xml-output-file-format-ssbdiagnose"></a>Формат выходного XML-файла (программа ssbdiagnose)
  Если запустить программу **ssbdiagnose** с параметром **-XML**, то выходные данные будут выданы в виде XML-файла. В выходном XML-файле содержатся заголовок и ошибки, обнаруженные в результате анализа конфигурации компонента [!INCLUDE[ssSB](../../includes/sssb-md.md)] или диалога. Для анализа ошибок, перечисленных в файле, и создания отчета по ним можно написать пользовательское приложение. Кроме того, XML-файл можно просмотреть в стандартном XML-редакторе, например в XML-блокноте.  
  
 Выходной файл программы **ssbdiangose** содержит корневой элемент DiagnosticInformation с двумя дочерними типами:  
  
-   элемент Banner с данными заголовка;  
  
-   элемент Issue для каждой проблемы, обнаруженной программой **ssbdiagnose**.  
  
## <a name="diagnosticinformation-root-element"></a>Корневой элемент DiagnosticInformation  
  
-   [Элемент DiagnosticInformation &#40;ssbdiagnose&#41;](diagnosticinformation-element-ssbdiagnose.md)  
  
## <a name="banner-element"></a>Элемент Banner  
  
-   [Элемент banner &#40;ssbdiagnose&#41;](banner-element-ssbdiagnose.md)  
  
## <a name="issue-element"></a>Элемент Issue  
  
-   [Элемент Issue &#40;ssbdiagnose&#41;](issue-element-ssbdiagnose.md)  
  
## <a name="see-also"></a>См. также  
 [Программа ssbdiagnose (компонент Service Broker)](ssbdiagnose-utility-service-broker.md)  
  
  
