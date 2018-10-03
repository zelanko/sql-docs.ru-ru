---
title: Тип данных ReportAction (ASSL) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- ReportAction Data Type
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- ReportAction
helpviewer_keywords:
- ReportAction data type
ms.assetid: b22f0d52-ed3a-4239-840e-0eaf172d7276
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: eb1679d0275e6662116976b572f612f9ab113bb1
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48164335"
---
# <a name="reportaction-data-type-assl"></a>Тип данных ReportAction (ASSL)
  Определяет производный тип данных, представляющий действие, создающее [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] отчета.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<ReportAction>  
   <!-- The following elements extend Action -->  
   <ReportServer>...</ReportServer>  
   <Path>...</Path>  
   <ReportParameters>...</ReportParameters>  
   <ReportFormatParameters>...</ReportFormatParameters>  
</ReportAction>  
```  
  
## <a name="data-type-characteristics"></a>Характеристики типа данных  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|Базовые типы данных|[Действие](action-data-type-assl.md)|  
|Производные типы данных|None|  
  
## <a name="data-type-relationships"></a>Связи типа данных  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительские элементы|None|  
|Дочерние элементы|[Путь](../properties/path-element-assl.md), [ReportFormatParameters](../collections/reportformatparameters-element-assl.md), [ReportParameters](../collections/reportparameters-element-assl.md), [ReportServer](../objects/server-element-assl.md)|  
|Производные элементы|[Действие](../objects/action-element-assl.md) ([действия](../collections/actions-element-assl.md) коллекцию [куба](../objects/cube-element-assl.md) или [перспективы](../objects/perspective-element-assl.md))|  
  
## <a name="remarks"></a>Примечания  
 Сервер отчетов отвечает на запросы с URL-адресами для отчетов. Действие по созданию отчета определяется с типом *Report*. Ресурсы и параметры отправляются на сервер при создании действия. Сервер представляет действие как действие типа «набор строк».  
  
 Соответствующий элемент в модели объектов объекты управления Analysis AMO — это <xref:Microsoft.AnalysisServices.ReportAction>.  
  
## <a name="see-also"></a>См. также  
 [Типы данных XML в языке сценариев служб аналитики &#40;ASSL&#41;](analysis-services-scripting-language-xml-data-types-assl.md)  
  
  
