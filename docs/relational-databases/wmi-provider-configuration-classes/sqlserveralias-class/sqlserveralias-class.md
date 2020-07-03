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
ms.openlocfilehash: 613df198c6278c43fce8de71c831aa017a82bcea
ms.sourcegitcommit: f7ac1976d4bfa224332edd9ef2f4377a4d55a2c9
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2020
ms.locfileid: "85888434"
---
# <a name="sqlserveralias-class"></a>Класс SqlServerAlias
[!INCLUDE [SQL Server](../../../includes/applies-to-version/sqlserver.md)]
  Класс [SqlServerAlias](../../../relational-databases/wmi-provider-configuration-classes/sqlserveralias-class/sqlserveralias-class.md) представляет псевдоним соединения сервера.  
  
 Псевдоним соединения сервера требуется при возникновении обоих следующих событий:  
  
-   Клиент подключается к экземпляру [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] по сетевому транспорту, который не является сетевым транспортом по умолчанию.  
  
-   экземпляр [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] , с которым соединяется клиент, прослушивает альтернативный именованный канал.  
  
 **Примечание.**[SqlServerAlias Class](../../../relational-databases/wmi-provider-configuration-classes/sqlserveralias-class/sqlserveralias-class.md) наследует метод **Put** из класса Provider. Однако он не возвращает результаты, как указано методом **Provider::Put** . Дополнительные сведения см. в документации WMI.  
  
## <a name="see-also"></a>См. также  
 [настройка клиентских протоколов](https://technet.microsoft.com/library/ms181035.aspx)  
  
  
