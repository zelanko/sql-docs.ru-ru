---
title: "Параметры командной строки (программа распределенного воспроизведения) средства администрирования | Документы Microsoft"
ms.custom: 
ms.date: 08/12/2016
ms.prod: sql-non-specified
ms.prod_service: sql-non-specified
ms.service: 
ms.component: distributed-replay
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c01b0ed3-67e4-4561-92d2-a8fbb086aca8
caps.latest.revision: "35"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: ae6edc607f16e822d2b752ee31c94042122007d7
ms.sourcegitcommit: b2d8a2d95ffbb6f2f98692d7760cc5523151f99d
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/05/2017
---
# <a name="administration-tool-command-line-options-distributed-replay-utility"></a>Параметры командной строки средства администрирования (программа распределенного воспроизведения)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)][!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Распределенного воспроизведения средство администрирования **DReplay.exe**, это средство командной строки для взаимодействия с контроллером распределенного воспроизведения. При помощи средства администрирования можно инициировать операции на контроллере, наблюдать за ними и отменять.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "значок ссылки на раздел") Дополнительные сведения о синтаксических обозначениях, используемых в синтаксисе средства администрирования см. в разделе [синтаксические обозначения Transact-SQL &#40; Transact-SQL &#41; ](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md).  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
dreplay {preprocess|replay|status|cancel} [options] [-?]}  
  
Usage:  
  
  dreplay preprocess [-m controller] -i input_trace_file  
    -d controller_working_dir [-c config_file] [-f status_interval]  
  
  dreplay replay [-m controller] -d controller_working_dir [-o]  
    [-s target_server] -w clients [-c config_file]  
    [-f status_interval]  
  
  dreplay status [-m controller] [-f status_interval]  
  
  dreplay cancel [-m controller] [-q]   
```  
  
## <a name="remarks"></a>Замечания  
 В программе **DReplay.exe**можно применять следующие параметры командной строки:  
  
 **preprocess**  
 Инициирует стадию предварительной обработки. Подготавливаются для воспроизведения на целевом сервере входные данные трассировки, отслеженные в рабочей среде.  
  
 **replay**  
 Инициирует стадию воспроизведения события. Данные воспроизведения отправляются указанным клиентам, запускается распределенное воспроизведение, синхронизируются клиенты. При необходимости каждый выбранный клиент может записывать последовательность воспроизведения и сохранять получившиеся файлы трассировки в локальном кэше.  
  
 **status**  
 Опрашивает контроллер и отображает его текущее состояние.  
  
 **cancel**  
 Отменяет текущую операцию, выполняемую на контроллере.  
  
 Подробные сведения о синтаксисе, включая командные аргументы и примеры, см. в следующих разделах:  
  
-   [Параметр предварительной обработки (средство администрирования распределенного воспроизведения)](../../tools/distributed-replay/preprocess-option-distributed-replay-administration-tool.md)  
  
-   [Параметр воспроизведения (средство администрирования распределенного воспроизведения)](../../tools/distributed-replay/replay-option-distributed-replay-administration-tool.md)  
  
-   [Параметр состояния (средство администрирования распределенного воспроизведения)](../../tools/distributed-replay/status-option-distributed-replay-administration-tool.md)  
  
-   [Параметр отмены (средство администрирования распределенного воспроизведения)](../../tools/distributed-replay/cancel-option-distributed-replay-administration-tool.md)  
  
 Удаленные вызовы процедур (RPC) воспроизводятся как RPC, а не события языка.  
  
## <a name="permissions"></a>Разрешения  
 Средство администрирования должно запускаться как интерактивный пользователь, с учетной записью локального пользователя или пользователя домена. Для использования учетной записи локального пользователя средство администрирования и контроллер должны быть запущены на одном компьютере.  
  
 Дополнительные сведения см. в статье [Distributed Replay Security](../../tools/distributed-replay/distributed-replay-security.md).  
  
## <a name="see-also"></a>См. также:  
 [Распределенное воспроизведение SQL Server](../../tools/distributed-replay/sql-server-distributed-replay.md)  
  
  
