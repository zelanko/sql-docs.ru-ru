---
title: Класс SqlServerAlias | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.topic: reference
api_name:
- SqlServerAlias Class
api_location:
- sqlmgmproviderxpsp2up.mof
topic_type:
- apiref
helpviewer_keywords:
- SqlServerAlias class
ms.assetid: 475662b9-6985-45bf-b1e9-b0f26ef50443
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.openlocfilehash: d913f28415c708ad09b419732ebef4e26b607ecb
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48221414"
---
# <a name="sqlserveralias-class"></a>Класс SqlServerAlias
  Класс [SqlServerAlias](sqlserveralias-class.md) представляет псевдоним соединения сервера.  
  
 Псевдоним соединения сервера требуется при возникновении обоих следующих событий:  
  
-   клиент соединяется с экземпляром [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] по сетевому средству передачи данных, не являющемуся сетевым транспортом по умолчанию;  
  
-   экземпляр [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] , с которым соединяется клиент, прослушивает альтернативный именованный канал.  
  
 **Примечание:** [класс SqlServerAlias](sqlserveralias-class.md) наследует `Put` метод из класса Provider. Однако он не возвращает результаты, как указано методом `Provider::Put`. Дополнительные сведения см. в документации WMI.  
  
## <a name="see-also"></a>См. также  
 [Настройка клиентских протоколов](http://technet.microsoft.com/library/ms181035.aspx)  
  
  
