---
title: Баннер элемент (ssbdiagnose) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
helpviewer_keywords:
- banner element
- XML output file format [ssbdiagnose], banner element
- ssbdiagnose
ms.assetid: cc6cd49a-acf0-4cfb-8c6a-554692b89de2
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: b461370b4bbab4cc7e28bcb1ed95d0a3e6d5553e
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48080744"
---
# <a name="banner-element-ssbdiagnose"></a>Элемент Banner (программа ssbdiagnose)
  Определяет программу, сформировавшую выходной XML-файл **ssbdiagnose** .  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
<Banner  
    title="..."   
    product="..."   
    version="..." />  
```  
  
## <a name="element-attributes"></a>Атрибуты элемента  
  
|attribute|Описание|  
|---------------|-----------------|  
|`title`|Определяет программу, сформировавшую выходной XML-файл **ssbdiagnose** .|  
|`product`|Определяет продукт, сформировавший выходной XML-файл **ssbdiagnose** .|  
|`version`|Определяет версию программы, которой был сформирован выходной XML-файл.|  
  
## <a name="element-characteristics"></a>Характеристики элемента  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|**Тип данных и длина**|Нет.|  
|**Значение по умолчанию**|Нет.|  
|**Наличие**|Один раз в каждом выходном XML-файле программы **ssbdiagnose** .|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элементы|  
|------------------|--------------|  
|**Родительский элемент**|[Элемент DiagnosticInformation &#40;ssbdiagnose&#41;](diagnosticinformation-element-ssbdiagnose.md)|  
|**Дочерние элементы**|Нет.|  
  
## <a name="example"></a>Пример  
 Ниже приведен пример элемента Banner.  
  
```  
<Banner title="Service Broker Diagnostics Utility" product="Microsoft SQL Server" version="10.0.1073.0" />  
```  
  
## <a name="see-also"></a>См. также  
 [Программа ssbdiagnose (компонент Service Broker)](ssbdiagnose-utility-service-broker.md)  
  
  
