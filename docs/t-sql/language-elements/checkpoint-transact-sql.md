---
title: "CHECKPOINT (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 07/27/2017
ms.prod: sql-non-specified
ms.prod_service: sql-database
ms.service: 
ms.component: t-sql|language-elements
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- CHECKPOINT_TSQL
- CHECKPOINT
dev_langs:
- TSQL
helpviewer_keywords:
- events [SQL Server], checkpoints
- automatic checkpoints
- writing dirty pages to disk
- pages [SQL Server], dirty
- checkpoints [SQL Server]
- CHECKPOINT statement
- log truncate mode [SQL Server]
- dirty pages
- logs [SQL Server], checkpoints
- manual checkpoints [SQL Server]
- pages [SQL Server], checkpoints
ms.assetid: ccdfc689-ad4e-44c0-83f7-0f2cfcfb6406
caps.latest.revision: 
author: barbkess
ms.author: barbkess
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 6353bd534827ff9066bd7b184a09d67b5867c3cb
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2018
---
# <a name="checkpoint-transact-sql"></a>CHECKPOINT (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Создает ручную контрольную точку в базе данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], с которой в данный момент установлено соединение.  
  
> [!NOTE]  
>  Сведения о различных типах контрольных точек базы данных и работе контрольных точек в целом см. в разделе [контрольные точки базы данных &#40; SQL Server &#41; ](../../relational-databases/logs/database-checkpoints-sql-server.md).  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
CHECKPOINT [ checkpoint_duration ]  
```  
  
## <a name="arguments"></a>Аргументы  
 *checkpoint_duration*  
 Задается запрашиваемое количество времени в секундах для завершения ручной контрольной точки. Когда *checkpoint_duration* указано, [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] пытается выполнить контрольную точку в течение запрашиваемого периода времени. *Checkpoint_duration* должен быть выражением типа **int** и должно быть больше нуля. Если этот аргумент опущен, компонент [!INCLUDE[ssDE](../../includes/ssde-md.md)] настраивает длительность выполнения контрольной точки таким образом, чтобы минимизировать влияние на производительность приложений базы данных. *checkpoint_duration* является дополнительным параметром.  
  
## <a name="factors-affecting-the-duration-of-checkpoint-operations"></a>Факторы, влияющие на длительность операций выполнения контрольных точек  
 Количество времени, необходимое для операции выполнения контрольной точки, увеличивается с возрастанием количества «грязных» страниц, которые необходимо записать операции. По умолчанию [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] регулирует частоту операций записи, которые выполняет контрольная точка, для минимизации влияния на производительность. Уменьшение частоты записи увеличивает время, необходимое для завершения операции выполнения контрольной точки. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]применяет эту стратегию ручную контрольную точку, если не *checkpoint_duration* значение указывается в команду CHECKPOINT.  
  
 Влияние на производительность с помощью *checkpoint_duration* зависящую от количества «грязных» страниц, уровня активности в системе и фактической задаваемой величины длительности. Например, если обычно для завершения контрольной точки будет в течение 120 секунд, указание *checkpoint_duration* величины 45 секунд ведет [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] чтобы выделять больше ресурсов для контрольной точки, чем количество по умолчанию. Напротив, указав *checkpoint_duration* 180 секунд для перевода [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] выделяет меньшее количество ресурсов, чем количество по умолчанию. В целом, меньшее *checkpoint_duration* ресурсов, выделяемых контрольной точке, приведет к увеличению при long *checkpoint_duration* уменьшит ресурсов, выделяемых контрольной точке. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] всегда, если это возможно, завершает обработку контрольной точки, а инструкция CHECKPOINT возвращает управление сразу же по завершении обработки контрольной точки. Следовательно, в некоторых случаях выполнение контрольной точки может завершиться быстрее, чем заданный период времени, или выполняться дольше этого периода.  
  
##  <a name="Security"></a> Безопасность  
  
### <a name="permissions"></a>Разрешения  
 Разрешения CHECKPOINT по умолчанию членам **sysadmin** предопределенной роли сервера и **db_owner** и **db_backupoperator** предопределенных ролей базы данных, а не могут передаваться.  
  
## <a name="see-also"></a>См. также  
 [ALTER DATABASE (Transact-SQL)](../../t-sql/statements/alter-database-transact-sql.md)   
 [Контрольные точки базы данных (SQL Server)](../../relational-databases/logs/database-checkpoints-sql-server.md)   
 [Настройка параметра конфигурации сервера recovery interval](../../database-engine/configure-windows/configure-the-recovery-interval-server-configuration-option.md)   
 [Завершение работы &#40; Transact-SQL &#41;](../../t-sql/language-elements/shutdown-transact-sql.md)  
  
  
