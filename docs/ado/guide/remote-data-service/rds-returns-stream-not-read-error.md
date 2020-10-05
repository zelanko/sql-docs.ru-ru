---
description: RDS возвращает &quot; ошибку "поток не прочитан" &quot;
title: RDS возвращает &quot; ошибку "поток не прочитан" &quot; | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: ado
ms.custom: ''
ms.date: 11/09/2018
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- stream not read error in RDS [ADO]
ms.assetid: cb5a68f8-dba4-41da-bafd-04efe53706b7
author: rothja
ms.author: jroth
ms.openlocfilehash: 6acb603594acdd23f8ad8764c9b9a692acabdb9b
ms.sourcegitcommit: c7f40918dc3ecdb0ed2ef5c237a3996cb4cd268d
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/05/2020
ms.locfileid: "91724905"
---
# <a name="rds-returns-quotstream-not-readquot-error"></a>RDS возвращает &quot; ошибку "поток не прочитан" &quot;
"Не удалось прочитать объект потока, поскольку он пуст, или текущая точка находится в конце потока. Для непустых потоков установите текущую точку с помощью свойства "расположение". Чтобы определить, пуст ли поток, проверьте свойство Size.  
  
 Если вы видите это сообщение об ошибке, возможно, вы попытались использовать параметризованный иерархический запрос по протоколу HTTP. RDS не позволяет использовать удаленные параметризованные иерархии.  
  
> [!IMPORTANT]
>  Начиная с Windows 8 и Windows Server 2012, компоненты RDS больше не включены в операционную систему Windows (Дополнительные сведения см. в статье о совместимости Windows 8 и [Windows server 2012 Cookbook](https://www.microsoft.com/download/details.aspx?id=27416) ). Клиентские компоненты RDS будут удалены в следующей версии Windows. Избегайте использования этого компонента в новых разработках и запланируйте изменение существующих приложений, в которых он применяется. Приложения, использующие RDS, должны переноситься в [службу данных WCF](/dotnet/framework/wcf/).  
  
## <a name="see-also"></a>См. также  
 [Основные принципы RDS](./rds-fundamentals.md)