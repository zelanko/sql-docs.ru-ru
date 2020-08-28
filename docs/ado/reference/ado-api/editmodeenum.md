---
description: EditModeEnum
title: Едитмодинум | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: ado
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
ms.openlocfilehash: 7e10479aca06eab4a7aa5215f0016dd1f82eab1c
ms.sourcegitcommit: 18a98ea6a30d448aa6195e10ea2413be7e837e94
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/27/2020
ms.locfileid: "88973855"
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
