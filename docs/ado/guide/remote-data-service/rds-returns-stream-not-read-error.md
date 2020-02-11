---
title: RDS возвращает &quot;ошибку "поток&quot; не прочитан" | Документация Майкрософт
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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: c89756e86a702217d5d9d8495bf62b0d27f52321
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "67922474"
---
# <a name="rds-returns-quotstream-not-readquot-error"></a>RDS возвращает &quot;ошибку "поток&quot; не прочитан"
"Не удалось прочитать объект потока, поскольку он пуст, или текущая точка находится в конце потока. Для непустых потоков установите текущую точку с помощью свойства "расположение". Чтобы определить, пуст ли поток, проверьте свойство Size.  
  
 Если вы видите это сообщение об ошибке, возможно, вы попытались использовать параметризованный иерархический запрос по протоколу HTTP. RDS не позволяет использовать удаленные параметризованные иерархии.  
  
> [!IMPORTANT]
>  Начиная с Windows 8 и Windows Server 2012, компоненты RDS больше не включены в операционную систему Windows (Дополнительные сведения см. в статье о совместимости Windows 8 и [Windows server 2012 Cookbook](https://www.microsoft.com/download/details.aspx?id=27416) ). Клиентские компоненты RDS будут удалены в следующей версии Windows. Избегайте использования этого компонента в новых разработках и запланируйте изменение существующих приложений, в которых он применяется. Приложения, использующие RDS, должны переноситься в [службу данных WCF](https://go.microsoft.com/fwlink/?LinkId=199565).  
  
## <a name="see-also"></a>См. также:  
 [Основные принципы RDS](../../../ado/guide/remote-data-service/rds-fundamentals.md)


