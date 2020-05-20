---
title: Формат выходного файла XML
description: В SQL Server служебная программа ssbdiagnose может предоставлять свои выходные данные в виде файла XML. Создайте приложение для анализа и отправки сообщений об ошибках или их просмотра в редакторе XML.
ms.prod: sql
ms.prod_service: sql-tools
ms.technology: tools-other
ms.topic: conceptual
helpviewer_keywords:
- XML output file format [ssbdiagnose]
- ssbdiagnose
ms.assetid: 3ceb991b-6f15-4504-8828-de5adf448bc5
author: markingmyname
ms.author: maghan
ms.manager: jroth
ms.reviewer: ''
ms.custom: seo-lt-2019
ms.date: 03/01/2017
ms.openlocfilehash: 1b039d5441ed39c85a8cf1e9468eddfe165aad1c
ms.sourcegitcommit: b8933ce09d0e631d1183a84d2c2ad3dfd0602180
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/13/2020
ms.locfileid: "83150509"
---
# <a name="xml-output-file-format-ssbdiagnose"></a>Формат выходного XML-файла (программа ssbdiagnose)

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

Если запустить программу **ssbdiagnose** с параметром **-XML** , то выходные данные будут выданы в виде XML-файла. В выходном XML-файле содержатся заголовок и ошибки, обнаруженные в результате анализа конфигурации компонента [!INCLUDE[ssSB](../../includes/sssb-md.md)] или диалога. Для анализа ошибок, перечисленных в файле, и создания отчета по ним можно написать пользовательское приложение. Кроме того, XML-файл можно просмотреть в стандартном XML-редакторе, например в XML-блокноте.  
  
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
  
  
