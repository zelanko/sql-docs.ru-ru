---
title: EditModeEnum | Документация Майкрософт
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 34583128e3da1bec00003fe194d3387783815275
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63181103"
---
# <a name="editmodeenum"></a>EditModeEnum
Указывает состояние редактирования записи.  
  
|Константа|Значение|Описание|  
|--------------|-----------|-----------------|  
|**как таковые**|0|Указывает, что ни одна из операций редактирования идет.|  
|**adEditInProgress**|1|Указывает, что данные в текущей записи были изменены, но не сохранены.|  
|**adEditAdd**|2|Указывает, что [AddNew](../../../ado/reference/ado-api/addnew-method-ado.md) был вызван метод, и текущую запись в буфер копирования считается новой записью, который не был сохранен в базе данных.|  
|**adEditDelete**|4|Указывает, что текущая запись была удалена.|  
  
## <a name="adowfc-equivalent"></a>Эквивалент ADO и WFC  
 Пакет: **com.ms.wfc.data**  
  
|Константа|  
|--------------|  
|AdoEnums.EditMode.NONE|  
|AdoEnums.EditMode.INPROGRESS|  
|AdoEnums.EditMode.ADD|  
|AdoEnums.EditMode.DELETE|  
  
## <a name="applies-to"></a>Объект применения  
 [Свойство EditMode](../../../ado/reference/ado-api/editmode-property.md)
