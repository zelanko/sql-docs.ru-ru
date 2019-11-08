---
title: Класс SqlServerAlias
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
apiname:
- SqlServerAlias Class
apilocation:
- sqlmgmproviderxpsp2up.mof
apitype: MOFDef
helpviewer_keywords:
- SqlServerAlias class
ms.assetid: 475662b9-6985-45bf-b1e9-b0f26ef50443
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 6cbcb2ab05c30f667e6e5b95d8223ab4e152137e
ms.sourcegitcommit: baa40306cada09e480b4c5ddb44ee8524307a2ab
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/06/2019
ms.locfileid: "73659186"
---
# <a name="sqlserveralias-class"></a>Класс SqlServerAlias
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]
  Класс [SqlServerAlias](../../../relational-databases/wmi-provider-configuration-classes/sqlserveralias-class/sqlserveralias-class.md) представляет псевдоним соединения сервера.  
  
 Псевдоним соединения сервера требуется при возникновении обоих следующих событий:  
  
-   клиент соединяется с экземпляром [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] по сетевому средству передачи данных, не являющемуся сетевым транспортом по умолчанию;  
  
-   экземпляр [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] , с которым соединяется клиент, прослушивает альтернативный именованный канал.  
  
 **Примечание.** [SqlServerAlias Class](../../../relational-databases/wmi-provider-configuration-classes/sqlserveralias-class/sqlserveralias-class.md) наследует метод **Put** из класса Provider. Однако он не возвращает результаты, как указано методом **Provider::Put** . Дополнительные сведения см. в документации WMI.  
  
## <a name="see-also"></a>См. также раздел  
 [Настройка клиентских протоколов](https://technet.microsoft.com/library/ms181035.aspx)  
  
  
