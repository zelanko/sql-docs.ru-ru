---
description: RDS возвращает &quot; ошибку "поток не прочитан" &quot;
title: RDS возвращает &quot; ошибку "поток не прочитан" &quot; | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 11/09/2018
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- stream not read error in RDS [ADO]
ms.assetid: cb5a68f8-dba4-41da-bafd-04efe53706b7
author: rothja
ms.author: jroth
ms.openlocfilehash: a0da62851a5cab542a64e219aecc70a13720570f
ms.sourcegitcommit: c4d564435c008e2c92035efd2658172f20f07b2b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/24/2020
ms.locfileid: "88759634"
---
# <a name="rds-returns-quotstream-not-readquot-error"></a>RDS возвращает &quot; ошибку "поток не прочитан" &quot;
"Не удалось прочитать объект потока, поскольку он пуст, или текущая точка находится в конце потока. Для непустых потоков установите текущую точку с помощью свойства "расположение". Чтобы определить, пуст ли поток, проверьте свойство Size.  
  
 Если вы видите это сообщение об ошибке, возможно, вы попытались использовать параметризованный иерархический запрос по протоколу HTTP. RDS не позволяет использовать удаленные параметризованные иерархии.  
  
> [!IMPORTANT]
>  Начиная с Windows 8 и Windows Server 2012, компоненты RDS больше не включены в операционную систему Windows (Дополнительные сведения см. в статье о совместимости Windows 8 и [Windows server 2012 Cookbook](https://www.microsoft.com/download/details.aspx?id=27416) ). Клиентские компоненты RDS будут удалены в следующей версии Windows. Избегайте использования этого компонента в новых разработках и запланируйте изменение существующих приложений, в которых он применяется. Приложения, использующие RDS, должны переноситься в [службу данных WCF](https://go.microsoft.com/fwlink/?LinkId=199565).  
  
## <a name="see-also"></a>См. также  
 [Основные принципы RDS](./rds-fundamentals.md)