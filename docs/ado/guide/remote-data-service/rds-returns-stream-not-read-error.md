---
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
ms.openlocfilehash: ca194c911b590dfcc8baba87195c91a70640dd24
ms.sourcegitcommit: 6037fb1f1a5ddd933017029eda5f5c281939100c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/04/2020
ms.locfileid: "82747741"
---
# <a name="rds-returns-quotstream-not-readquot-error"></a>RDS возвращает &quot; ошибку "поток не прочитан" &quot;
"Не удалось прочитать объект потока, поскольку он пуст, или текущая точка находится в конце потока. Для непустых потоков установите текущую точку с помощью свойства "расположение". Чтобы определить, пуст ли поток, проверьте свойство Size.  
  
 Если вы видите это сообщение об ошибке, возможно, вы попытались использовать параметризованный иерархический запрос по протоколу HTTP. RDS не позволяет использовать удаленные параметризованные иерархии.  
  
> [!IMPORTANT]
>  Начиная с Windows 8 и Windows Server 2012, компоненты RDS больше не включены в операционную систему Windows (Дополнительные сведения см. в статье о совместимости Windows 8 и [Windows server 2012 Cookbook](https://www.microsoft.com/download/details.aspx?id=27416) ). Клиентские компоненты RDS будут удалены в следующей версии Windows. Избегайте использования этого компонента в новых разработках и запланируйте изменение существующих приложений, в которых он применяется. Приложения, использующие RDS, должны переноситься в [службу данных WCF](https://go.microsoft.com/fwlink/?LinkId=199565).  
  
## <a name="see-also"></a>См. также  
 [Основные принципы RDS](../../../ado/guide/remote-data-service/rds-fundamentals.md)


