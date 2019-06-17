---
title: Параметры командной строки средства администрирования (программа распределенного воспроизведения) | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: tools-other
ms.topic: conceptual
ms.assetid: c01b0ed3-67e4-4561-92d2-a8fbb086aca8
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: f53c456832e89aa96c0f7c9a1decd9fabbe96360
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "63151585"
---
# <a name="administration-tool-command-line-options-distributed-replay-utility"></a>Параметры командной строки средства администрирования (программа распределенного воспроизведения)
  [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Средство администрирования распределенного воспроизведения `DReplay.exe`, это средство командной строки, которое можно использовать для взаимодействия с контроллером распределенного воспроизведения. При помощи средства администрирования можно инициировать операции на контроллере, наблюдать за ними и отменять.  
  
 ![Topic link icon](../../database-engine/media/topic-link.gif "Значок ссылки на раздел") Дополнительные сведения о синтаксических обозначениях, используемых в синтаксисе средства администрирования, см. в разделе [Синтаксические обозначения в Transact-SQL (Transact-SQL)](/sql/t-sql/language-elements/transact-sql-syntax-conventions-transact-sql).  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
      dreplay {preprocess|replay|status|cancel} [options] [-?]}  
  
Usage:  
  
  dreplay preprocess [-mcontroller] -iinput_trace_file  
    -dcontroller_working_dir [-cconfig_file] [-fstatus_interval]  
  
  dreplay replay [-mcontroller] -dcontroller_working_dir [-o]  
    [-starget_server] -wclients [-cconfig_file]  
    [-fstatus_interval]  
  
  dreplay status [-mcontroller] [-fstatus_interval]  
  
  dreplay cancel [-mcontroller] [-q]   
```  
  
## <a name="remarks"></a>Примечания  
 В программе `DReplay.exe` можно применять следующие параметры командной строки:  
  
 **preprocess**  
 Инициирует стадию предварительной обработки. Подготавливаются для воспроизведения на целевом сервере входные данные трассировки, отслеженные в рабочей среде.  
  
 **replay**  
 Инициирует стадию воспроизведения события. Данные воспроизведения отправляются указанным клиентам, запускается распределенное воспроизведение, синхронизируются клиенты. При необходимости каждый выбранный клиент может записывать последовательность воспроизведения и сохранять получившиеся файлы трассировки в локальном кэше.  
  
 **status**  
 Опрашивает контроллер и отображает его текущее состояние.  
  
 **cancel**  
 Отменяет текущую операцию, выполняемую на контроллере.  
  
 Подробные сведения о синтаксисе, включая командные аргументы и примеры, см. в следующих разделах:  
  
-   [Параметр предварительной обработки (средство администрирования распределенного воспроизведения)](preprocess-option-distributed-replay-administration-tool.md)  
  
-   [Параметр воспроизведения (средство администрирования распределенного воспроизведения)](replay-option-distributed-replay-administration-tool.md)  
  
-   [Параметр состояния (средство администрирования распределенного воспроизведения)](status-option-distributed-replay-administration-tool.md)  
  
-   [Параметр отмены (средство администрирования распределенного воспроизведения)](cancel-option-distributed-replay-administration-tool.md)  
  
 Удаленные вызовы процедур (RPC) воспроизводятся как RPC, а не события языка.  
  
## <a name="permissions"></a>Разрешения  
 Средство администрирования должно запускаться как интерактивный пользователь, с учетной записью локального пользователя или пользователя домена. Для использования учетной записи локального пользователя средство администрирования и контроллер должны быть запущены на одном компьютере.  
  
 Дополнительные сведения см. в статье [Distributed Replay Security](distributed-replay-security.md).  
  
## <a name="see-also"></a>См. также  
 [Распределенное воспроизведение SQL Server](sql-server-distributed-replay.md)  
  
  
