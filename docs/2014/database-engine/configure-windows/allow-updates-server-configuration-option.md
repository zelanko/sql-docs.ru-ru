---
title: Параметр конфигурации сервера "allow updates" | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- allow updates option
ms.assetid: 3967c3ed-280a-4de8-a2ce-393e82745a7b
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 6cf28b18bcad06be7383b98dee72810c4e6157c0
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2020
ms.locfileid: "62786993"
---
# <a name="allow-updates-server-configuration-option"></a>Параметр конфигурации сервера «allow updates»
  Этот параметр по-прежнему присутствует в хранимой процедуре **sp_configure** , хотя его функции недоступны в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Параметр не влияет на работу сервера. Непосредственные обновления системных таблиц не поддерживаются.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)]  
  
 Изменение параметра **allow updates** приведет к сбою при выполнении инструкции RECONFIGURE. Изменения параметра **allow updates** необходимо удалить из всех скриптов.  
  
## <a name="see-also"></a>См. также:  
 [Параметры конфигурации сервера (SQL Server)](server-configuration-options-sql-server.md)  
  
  
