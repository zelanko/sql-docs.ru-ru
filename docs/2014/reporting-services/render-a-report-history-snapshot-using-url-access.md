---
title: Обработка моментального снимка журнала отчета с использованием доступа по URL-адресу | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- URL access [Reporting Services], report history
- history snapshots [Reporting Services]
- historical data [Reporting Services]
- snapshots [Reporting Services], URL access
- snapshots [Reporting Services], rendering report history
ms.assetid: 3f87f82d-0e61-4492-9c4b-f5238c39e8cd
caps.latest.revision: 32
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: b065fa70d102ff86c25aa0fffb78cfa4993cd284
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37272580"
---
# <a name="render-a-report-history-snapshot-using-url-access"></a>Обработка моментального снимка журнала отчета с использованием доступа по URL-адресу
  Подготовить отчет к просмотру можно с помощью моментального снимка журнала отчета. Для этого необходимо указать параметр *rs:Snapshot* и присвоить ему значение допустимого идентификатора моментального снимка. Значение параметра должно указываться в формате ГГГГ-ММ-ДДТЧЧ:ММ:СС согласно стандарту Международной организации по стандартизации (ISO) 8601.  
  
 Если этот параметр не указан, то отчет подготавливается к просмотру согласно параметрам его выполнения и параметрам управления кэшем на сервере отчетов. Дополнительные сведения о выполнении отчетов см. в разделе [Установка свойств обработки отчетов](report-server/set-report-processing-properties.md).  
  
## <a name="example"></a>Пример  
 В приведенном ниже примере показан URL-адрес, по которому происходит получение моментального снимка журнала отчета.  
  
```  
http://myrshost/reportserver?/SampleReports/Company Sales&rs:Snapshot=2003-04-07T13:40:02  
```  
  
## <a name="see-also"></a>См. также  
 [URL-адресов &#40;SSRS&#41;](url-access-ssrs.md)   
 [Ссылка на параметр доступа по URL-адресу](url-access-parameter-reference.md)  
  
  
