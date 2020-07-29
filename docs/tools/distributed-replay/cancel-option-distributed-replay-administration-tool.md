---
title: Параметр cancel в средстве администрирования
titleSuffix: SQL Server Distributed Replay
description: В этой статье описывается параметр командной строки cancel и синтаксис средства администрирования распределенного воспроизведения Microsoft SQL Server.
ms.custom: seo-lt-2019
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.technology: tools-other
ms.topic: conceptual
ms.assetid: fea376de-307a-4b45-b7e2-37df88f3681a
author: markingmyname
ms.author: maghan
ms.openlocfilehash: 1637e6c8130ab8361b54617fddcba0fc51e54b3a
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/01/2020
ms.locfileid: "85681870"
---
# <a name="cancel-option-distributed-replay-administration-tool"></a>Параметр отмены (средство администрирования распределенного воспроизведения)

 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

Средство администрирования распределенного воспроизведения [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (**DReplay.exe**) представляет собой программу командной строки, которая служит для взаимодействия с контроллером распределенного воспроизведения. В этом разделе описывается параметр командной строки **cancel** и соответствующий синтаксис.  
  
 Параметр **cancel** отменяет текущую операцию, выполняемую на контроллере.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") Дополнительные сведения о синтаксических обозначениях, используемых в синтаксисе средства администрирования, см. в разделе [Синтаксические обозначения в Transact-SQL (Transact-SQL)](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md).  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
dreplay cancel [-m controller] [-q]   
```  
  
#### <a name="parameters"></a>Параметры  
 **-m** *controller*  
 Имя компьютера для контроллера. Локальный компьютер можно указать как «`localhost`» или «`.`».  
  
 Если параметр **-m** не задан, то используется локальный компьютер.  
  
 **-q**  
 Тихий режим. Не запрашивает подтверждения.  
  
 Параметр **-q** необязателен.  
  
## <a name="examples"></a>Примеры  
 В следующем примере запрос отмены передается в тихом режиме. Значение `localhost` указывает, что служба контроллера запущена на том же компьютере, что и средство администрирования.  
  
```  
dreplay cancel -m localhost -q  
```  
  
## <a name="permissions"></a>Разрешения  
 Средство администрирования должно запускаться как интерактивный пользователь, с учетной записью локального пользователя или пользователя домена. Для использования учетной записи локального пользователя средство администрирования и контроллер должны быть запущены на одном компьютере.  
  
 Дополнительные сведения см. в статье [Distributed Replay Security](../../tools/distributed-replay/distributed-replay-security.md).  
  
## <a name="see-also"></a>См. также:  
 [Распределенное воспроизведение SQL Server](../../tools/distributed-replay/sql-server-distributed-replay.md)  
  
  
