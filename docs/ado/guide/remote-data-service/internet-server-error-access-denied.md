---
title: 'Ошибка сервера Интернета: доступ запрещен | Документация Майкрософт'
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 11/09/2018
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- access denied error in RDS [ADO]
ms.assetid: e5b43cfa-da8d-430d-a2ab-5443dda47a16
author: rothja
ms.author: jroth
ms.openlocfilehash: 93761afa168d8b6b2cd06cf5e1360d54fa5177c6
ms.sourcegitcommit: 6037fb1f1a5ddd933017029eda5f5c281939100c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/04/2020
ms.locfileid: "82749500"
---
# <a name="internet-server-error-access-denied"></a>Ошибка сервера Интернета: доступ запрещен
Если возникает эта ошибка, обычно это означает, что Microsoft службы IIS (IIS) вернул следующее состояние:  
  
 HTTP_STATUS_DENIED 401  
  
 Убедитесь, что каталоги, к которым имеют доступ IIS, имеют соответствующие разрешения. RDS может взаимодействовать с веб-сервером IIS, работающим в любом из трех режимов проверки подлинности паролей: анонимный, базовый или NT запрос/ответ (это называется встроенной проверкой подлинности Windows в Windows 2000). Кроме того, веб-сервер должен иметь разрешения на компьютер источника данных, если это компьютер под управлением Windows NT или Windows 2000.  
  
> [!IMPORTANT]
>  Начиная с Windows 8 и Windows Server 2012, компоненты RDS больше не включены в операционную систему Windows (Дополнительные сведения см. в статье о совместимости Windows 8 и [Windows server 2012 Cookbook](https://www.microsoft.com/download/details.aspx?id=27416) ). Клиентские компоненты RDS будут удалены в следующей версии Windows. Избегайте использования этого компонента в новых разработках и запланируйте изменение существующих приложений, в которых он применяется. Приложения, использующие RDS, должны переноситься в [службу данных WCF](https://go.microsoft.com/fwlink/?LinkId=199565).  
  
## <a name="see-also"></a>См. также  
 [Основные принципы RDS](../../../ado/guide/remote-data-service/rds-fundamentals.md)




