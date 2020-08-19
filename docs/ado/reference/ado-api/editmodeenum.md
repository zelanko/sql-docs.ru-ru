---
description: EditModeEnum
title: Едитмодинум | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- EditModeEnum
helpviewer_keywords:
- EditModeEnum enumeration [ADO]
ms.assetid: 45d54b6e-db2c-4553-9fd0-528147d6da2f
author: rothja
ms.author: jroth
ms.openlocfilehash: 64310c3399d24d557fc0896587dad0dc4fde091b
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88444046"
---
# <a name="editmodeenum"></a>EditModeEnum
Указывает состояние редактирования записи a.  
  
|Константа|Значение|Описание|  
|--------------|-----------|-----------------|  
|**адедитноне**|0|Указывает, что операции редактирования не выполняются.|  
|**адедитинпрогресс**|1|Указывает, что данные в текущей записи были изменены, но не сохранены.|  
|**адедитадд**|2|Указывает, что был вызван метод [AddNew](../../../ado/reference/ado-api/addnew-method-ado.md) , а текущая запись в буфере копирования является новой записью, которая не была сохранена в базе данных.|  
|**адедитделете**|4|Указывает, что текущая запись была удалена.|  
  
## <a name="adowfc-equivalent"></a>Эквивалент ADO/WFC  
 Пакет: **com. MS. WFC. Data**  
  
|Константа|  
|--------------|  
|Адоенумс. EditMode. NONE|  
|Адоенумс. EditMode. выполняется|  
|Адоенумс. EditMode. ADD|  
|Адоенумс. EditMode. DELETE|  
  
## <a name="applies-to"></a>Применение  
 [Свойство EditMode](../../../ado/reference/ado-api/editmode-property.md)
