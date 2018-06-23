---
title: Элемент Password (XML для Аналитики) | Документы Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
api_name:
- Password Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- http://schemas.microsoft.com/analysisservices/2003/engine#Password
- urn:schemas-microsoft-com:xml-analysis#Password
- microsoft.xml.analysis.password
helpviewer_keywords:
- Password element
ms.assetid: 8a0603bd-f6a1-4b86-84f1-c83d0b03951b
caps.latest.revision: 11
author: mgblythe
ms.author: mblythe
manager: mblythe
ms.openlocfilehash: cfc62de4ad73888fb95fe179efd0fdaeabbc9dc9
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36102509"
---
# <a name="password-element-xmla"></a>Элемент Password (XML для аналитики)
  Определяет пароль, который будет использоваться родительской [резервного копирования](../xml-elements-commands/backup-element-xmla.md) или [восстановить](../xml-elements-commands/restore-element-xmla.md) команду для шифрования или расшифрования файла резервной копии.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<Backup> <!-- or Restore -->  
   ...  
   <Password>...</Password>  
   ...  
</Backup>  
```  
  
## <a name="element-characteristics"></a>Характеристики элемента  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|Тип данных и длина|String|  
|Значение по умолчанию|None|  
|Количество элементов|0-1: необязательный элемент, который может встречаться только один раз.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительские элементы|[Резервное копирование](../xml-elements-commands/backup-element-xmla.md), [восстановления](../xml-elements-commands/restore-element-xmla.md)|  
|Дочерние элементы|None|  
  
## <a name="remarks"></a>Примечания  
 Если при выполнении команды `Backup` не был включен элемент `Password` или он содержит пустую строку, то файл резервной копии не будет зашифрован.  
  
 Если при выполнении команды `Restore` не был включен элемент `Password` или он содержит пустую строку, то при попытке восстановления зашифрованного файла резервной копии возникнет ошибка.  
  
 Если при выполнении команды `Location` или `Backup` был включен элемент `Restore`, то для обычного и удаленного файлов резервной копии будет использован один и тот же элемент `Password`. Дополнительные сведения об удаленных файлах резервных копий см. в разделе [резервное копирование, восстановление и синхронизация баз данных &#40;XMLA&#41;](../../multidimensional-models-scripting-language-assl-xmla/backing-up-restoring-and-synchronizing-databases-xmla.md).  
  
## <a name="see-also"></a>См. также  
 [Элемент Location &#40;XML для Аналитики&#41;](location-element-xmla.md)   
 [Свойства &#40;XML для Аналитики&#41;](xml-elements-properties.md)  
  
  