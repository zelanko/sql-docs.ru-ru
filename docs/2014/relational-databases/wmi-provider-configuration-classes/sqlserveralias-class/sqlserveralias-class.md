---
title: Класс SqlServerAlias | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
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
ms.openlocfilehash: 46994409cc6a5119c9144eb7a3a4b9a8a9a22c44
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/18/2020
ms.locfileid: "85002454"
---
# <a name="sqlserveralias-class"></a>Класс SqlServerAlias
  Класс [SqlServerAlias](sqlserveralias-class.md) представляет псевдоним соединения сервера.  
  
 Псевдоним соединения сервера требуется при возникновении обоих следующих событий:  
  
-   Клиент подключается к экземпляру [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] по сетевому транспорту, который не является сетевым транспортом по умолчанию.  
  
-   экземпляр [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] , с которым соединяется клиент, прослушивает альтернативный именованный канал.  
  
 **Примечание.** [Класс SqlServerAlias](sqlserveralias-class.md) наследует `Put` метод от класса поставщика. Однако он не возвращает результаты, как указано методом `Provider::Put`. Дополнительные сведения см. в документации WMI.  
  
## <a name="see-also"></a>См. также:  
 [настройка клиентских протоколов](https://technet.microsoft.com/library/ms181035.aspx)  
  
  
