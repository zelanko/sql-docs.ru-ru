---
description: Ошибки (ADO)
title: Ошибки (ADO) | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- OLE DB providers [ADO]
- ADO, OLE DB providers
ms.assetid: 8ae6611b-3069-4155-b014-c0c9da37be39
author: rothja
ms.author: jroth
ms.openlocfilehash: 392d1f2fdfc0a7fe2e0cf9e1e14efb77f396acfd
ms.sourcegitcommit: 33e774fbf48a432485c601541840905c21f613a0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/25/2020
ms.locfileid: "88806124"
---
# <a name="errors-ado"></a>Ошибки (ADO)
Любая операция, включающая объекты ADO, может формировать одну или несколько ошибок поставщика. При возникновении каждой ошибки в коллекцию **ошибок** объекта **Connection** помещаются один или несколько объектов **ошибок** . Дополнительные сведения об обработке предупреждений и ошибок в приложении ADO см. в разделе [Обработка ошибок](./error-handling.md).  
  
 Ошибки приложения могут вызываться отдельным механизмом. Например, в Visual Basic объект **Err** будет содержать ошибки уровня приложения.