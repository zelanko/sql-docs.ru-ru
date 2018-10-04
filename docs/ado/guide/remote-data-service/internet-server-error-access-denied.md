---
title: 'Ошибка сервера Интернета: Доступ запрещен | Документация Майкрософт'
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- access denied error in RDS [ADO]
ms.assetid: e5b43cfa-da8d-430d-a2ab-5443dda47a16
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 6d7932d5d30964e654f86138a02977a27521569b
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47681530"
---
# <a name="internet-server-error-access-denied"></a>Ошибка сервера Интернета: доступ запрещен
Если вы получаете эту ошибку, это обычно означает, что Microsoft Internet Information Services (IIS) возвращено следующее состояние:  
  
 HTTP_STATUS_DENIED 401  
  
 Убедитесь, что каталоги, доступ к IIS имеют соответствующие разрешения. Служба удаленных рабочих СТОЛОВ может взаимодействовать с веб-сервер IIS под управлением в одном из трех режимов проверки подлинности пароля: анонимный, Basic или NT вызов-ответ (называемый Windows интегрированной проверки подлинности в Windows 2000). Кроме того веб-сервера необходимы разрешения на компьютер источника данных, если это компьютер с Windows NT и Windows 2000.  
  
> [!IMPORTANT]
>  Начиная с Windows 8 и Windows Server 2012, серверные компоненты служб удаленных рабочих СТОЛОВ, больше не включаются в операционной системе Windows (см. в разделе Windows 8 и [настольная книга по совместимости Windows Server 2012](https://www.microsoft.com/en-us/download/details.aspx?id=27416) для получения дополнительных сведений). Клиентские компоненты служб удаленных рабочих СТОЛОВ будет поддерживаться в будущих версиях Windows. Избегайте использования этого компонента в новых разработках и запланируйте изменение существующих приложений, в которых он применяется. Приложения, использующие служб удаленных рабочих СТОЛОВ, следует перевести [WCF-сервиса данных](http://go.microsoft.com/fwlink/?LinkId=199565).  
  
## <a name="see-also"></a>См. также  
 [Основные принципы RDS](../../../ado/guide/remote-data-service/rds-fundamentals.md)




