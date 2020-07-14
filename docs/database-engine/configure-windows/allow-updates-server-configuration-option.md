---
title: Параметр конфигурации сервера "allow updates" | Документы Майкрософт
description: Сведения об устаревшем параметре конфигурации SQL Server allow updates. Информация о том, в каких случаях при его применении выполнение инструкций RECONFIGURE завершается сбоем.
ms.custom: ''
ms.date: 03/02/2017
ms.prod: sql
ms.prod_service: high-availability
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- allow updates option
ms.assetid: 3967c3ed-280a-4de8-a2ce-393e82745a7b
author: markingmyname
ms.author: maghan
ms.openlocfilehash: 6e4cde898f4b7c95fa3dd46d23d073ba47b5fb43
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/01/2020
ms.locfileid: "85725263"
---
# <a name="allow-updates-server-configuration-option"></a>Параметр конфигурации сервера «allow updates»
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Этот параметр по-прежнему присутствует в хранимой процедуре **sp_configure** , хотя его функции недоступны в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Параметр не влияет на работу сервера. Непосредственные обновления системных таблиц не поддерживаются.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)]  
  
 Изменение параметра **allow updates** приведет к сбою при выполнении инструкции RECONFIGURE. Изменения параметра **allow updates** необходимо удалить из всех скриптов.  
  
## <a name="see-also"></a>См. также:  
 [Параметры конфигурации сервера (SQL Server)](../../database-engine/configure-windows/server-configuration-options-sql-server.md)  
  
  
