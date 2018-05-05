---
title: EditModeEnum | Документы Microsoft
ms.prod: sql
ms.prod_service: connectivity
ms.component: ado
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- EditModeEnum
helpviewer_keywords:
- EditModeEnum enumeration [ADO]
ms.assetid: 45d54b6e-db2c-4553-9fd0-528147d6da2f
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: ba6822bfbb45ee547b87c56388b55d95195a7b63
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="editmodeenum"></a>EditModeEnum
Указывает состояние редактирования записи.  
  
|Константа|Значение|Описание|  
|--------------|-----------|-----------------|  
|**как таковые**|0|Указывает, что ни одна из операций редактирования идет.|  
|**adEditInProgress**|1|Указывает, что данные в текущей записи были изменены, но не сохранены.|  
|**adEditAdd**|2|Указывает, что [AddNew](../../../ado/reference/ado-api/addnew-method-ado.md) был вызван метод, и текущую запись в буфер копирования считается новой записью, не были сохранены в базе данных.|  
|**adEditDelete**|4|Указывает, что текущая запись была удалена.|  
  
## <a name="adowfc-equivalent"></a>Эквивалент ADO/WFC  
 Пакет: **com.ms.wfc.data**  
  
|Константа|  
|--------------|  
|AdoEnums.EditMode.NONE|  
|AdoEnums.EditMode.INPROGRESS|  
|AdoEnums.EditMode.ADD|  
|AdoEnums.EditMode.DELETE|  
  
## <a name="applies-to"></a>Объект применения  
 [Свойство EditMode](../../../ado/reference/ado-api/editmode-property.md)
