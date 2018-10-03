---
title: Элемент Administer (ASSL) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- Administer Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- Administer
helpviewer_keywords:
- Administer element
ms.assetid: 52924cd6-6176-47c8-ab17-4ee0e0ce42b1
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 682c65420383bcd3db70d1c477781c7db1193334
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48149304"
---
# <a name="administer-element-assl"></a>Элемент Administer (ASSL)
  Указывает, включает ли связанное разрешение право администрировать [базы данных](../objects/database-element-assl.md) элемент.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<DatabasePermission>  
      ...  
      <Administer>...</Administer>  
   ...  
</DatabasePermission>  
```  
  
## <a name="element-characteristics"></a>Характеристики элемента  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|Тип данных и длина|Логическое значение|  
|Значение по умолчанию|False|  
|Количество элементов|0-1: необязательный элемент, который может встречаться только один раз.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительские элементы|[DatabasePermission](../objects/databasepermission-element-assl.md)|  
|Дочерние элементы|None|  
  
## <a name="remarks"></a>Примечания  
 Элемент `Administer` показывает, может ли пользователь выполнять административные функции только в отношении указанной базы данных. Роль администратора сервера позволяет выполнять административные функции во всех базах данных экземпляра.  
  
 Элемент, соответствующий родителю параметра `Administer` в объекты управления Analysis AMO объектной модели это <xref:Microsoft.AnalysisServices.DatabasePermission>.  
  
## <a name="see-also"></a>См. также  
 [Тип данных Permission &#40;ASSL&#41;](../data-type/permission-data-type-assl.md)   
 [Элемент Role &#40;ASSL&#41;](../objects/role-element-assl.md)   
 [Свойства &#40;ASSL&#41;](properties-assl.md)  
  
  
