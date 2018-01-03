---
title: "EditModeEnum | Документы Microsoft"
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: ado
ms.technology: drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
apitype: COM
f1_keywords: EditModeEnum
helpviewer_keywords: EditModeEnum enumeration [ADO]
ms.assetid: 45d54b6e-db2c-4553-9fd0-528147d6da2f
caps.latest.revision: "11"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 6d5f1463191ced2f9e4768193ae5c79c5619896a
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/21/2017
---
# <a name="editmodeenum"></a>EditModeEnum
Указывает состояние редактирования записи.  
  
|Константа|Значение|Description|  
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
