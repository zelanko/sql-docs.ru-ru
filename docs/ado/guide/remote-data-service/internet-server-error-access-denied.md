---
title: "Интернет-ошибка сервера: Отказано в доступе | Документы Microsoft"
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: guide
ms.technology: drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: access denied error in RDS [ADO]
ms.assetid: e5b43cfa-da8d-430d-a2ab-5443dda47a16
caps.latest.revision: "15"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: ad54a40b51084bbf17c754521d914e08222408bb
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="internet-server-error-access-denied"></a>Интернет-ошибка сервера: Отказано в доступе
Если эта ошибка появляется, это обычно означает, что Microsoft Internet Information Services (IIS) возвращены следующие состояния:  
  
 HTTP_STATUS_DENIED 401  
  
 Убедитесь, что каталогов, доступных в службах IIS имеются надлежащие разрешения. Служб удаленных рабочих СТОЛОВ может взаимодействовать с веб-сервер IIS под управлением в одном из трех режимов проверки подлинности пароль: анонимный, Basic или NT Challenge/Response (называемых встроенную проверку подлинности Windows в Windows 2000). Кроме того веб-сервера требуются разрешения на компьютер источника данных, если он является компьютером Windows NT и Windows 2000.  
  
> [!IMPORTANT]
>  Начиная с Windows 8 и Windows Server 2012, серверные компоненты служб удаленных рабочих СТОЛОВ больше не включаются в операционной системе Windows (в разделе Windows 8 и [руководство по Windows Server 2012 совместимости](https://www.microsoft.com/en-us/download/details.aspx?id=27416) для получения дополнительных сведений). Клиентские компоненты служб удаленных рабочих СТОЛОВ будут удалены в будущих версиях Windows. Избегайте использования этого компонента в новых разработках и запланируйте изменение существующих приложений, в которых он применяется. Приложения, использующие служб удаленных рабочих СТОЛОВ необходимо перенести в [службы данных WCF](http://go.microsoft.com/fwlink/?LinkId=199565).  
  
## <a name="see-also"></a>См. также:  
 [Основные принципы RDS](../../../ado/guide/remote-data-service/rds-fundamentals.md)




