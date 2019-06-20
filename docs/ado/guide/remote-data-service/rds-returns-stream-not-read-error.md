---
title: RDS возвращает &quot;Stream не чтения&quot; ошибка | Документация Майкрософт
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
manager: jroth
ms.openlocfilehash: 598326335c32f18b5d7f5a764d387e5b5ea536f6
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "66699428"
---
# <a name="rds-returns-quotstream-not-readquot-error"></a>RDS возвращает &quot;Stream не чтения&quot; ошибки
«Объект Stream не удалось прочитать, так как он пуст или текущая позиция находится в конце Stream. Для потоков не пустой установите текущее положение с помощью свойства Position. Чтобы определить, пуста ли Stream, проверьте свойство размера.»  
  
 Если вы видите это сообщение об ошибке, предпринята использование параметризованного запроса иерархических по протоколу http. Служба удаленных рабочих СТОЛОВ позволяет использовать удаленный параметризованные иерархии.  
  
> [!IMPORTANT]
>  Начиная с Windows 8 и Windows Server 2012, серверные компоненты служб удаленных рабочих СТОЛОВ, больше не включаются в операционной системе Windows (см. в разделе Windows 8 и [настольная книга по совместимости Windows Server 2012](https://www.microsoft.com/download/details.aspx?id=27416) для получения дополнительных сведений). Клиентские компоненты служб удаленных рабочих СТОЛОВ будет поддерживаться в будущих версиях Windows. Избегайте использования этого компонента в новых разработках и запланируйте изменение существующих приложений, в которых он применяется. Приложения, использующие служб удаленных рабочих СТОЛОВ, следует перевести [WCF-сервиса данных](https://go.microsoft.com/fwlink/?LinkId=199565).  
  
## <a name="see-also"></a>См. также  
 [Основные принципы RDS](../../../ado/guide/remote-data-service/rds-fundamentals.md)


