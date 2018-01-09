---
title: "Подготовка команд | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: native-client-ole-db-commands
ms.reviewer: 
ms.suite: sql
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- SQL Server Native Client OLE DB provider, commands
- prepared statements [SQL Server Native Client]
- commands [OLE DB]
- command preparation [SQL Server Native Client]
ms.assetid: 09ec0c6c-0a44-4766-b9b7-5092f676ee54
caps.latest.revision: "31"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: ded4d70ef9067f9aff00b55920fc673944d6dfaa
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/08/2018
---
# <a name="preparing-commands"></a>Подготовка команд
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  Поставщик OLE DB для собственного клиента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поддерживает подготовку команды для оптимизированного многократного выполнения, однако подготовка команды создает дополнительную нагрузку; поэтому потребителю нет необходимости подготавливать команду для ее выполнения более одного раза. Как правило, подготовку команды следует выполнять в том случае, если планируется ее не менее чем четырехкратное выполнение.  
  
 По соображениям производительности подготовка команды откладывается до ее выполнения. Это поведение по умолчанию. Об ошибках, содержащихся в подготавливаемой команде, не будет ничего известно до ее выполнения или до выполнения операции с метасвойством. При установке свойства [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] SSPROP_DEFERPREPARE в значение FALSE это поведение по умолчанию может быть отключено.  
  
 Если команда выполняется напрямую (без предварительной подготовки), то [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] создает и кэширует план выполнения. При повторном выполнении инструкции SQL [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] применяет эффективный алгоритм сопоставления новой инструкции с существующим планом выполнения и повторно использует для этой инструкции тот же план выполнения.  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] предусматривает встроенную поддержку подготавливаемых и выполняемых инструкций. При подготовке инструкции [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] создает план выполнения, кэширует его и возвращает поставщику дескриптор этого плана. Поставщик пользуется этим дескриптором для повторного выполнения инструкции. Хранимые процедуры не создаются. Поскольку дескриптор прямо указывает на план выполнения инструкции SQL, а не сопоставляет инструкцию с планом выполнения, содержащимся в кэше (как при прямом выполнении), значительно эффективнее выполнить подготовку инструкции, а не выполнять ее напрямую, если известно, что инструкция будет использоваться многократно.  
  
 В [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] подготовленные инструкции не могут применяться для создания временных объектов (например, временных таблиц) и не могут ссылаться на создающие их системные хранимые процедуры. Эти процедуры следует выполнять напрямую.  
  
 Некоторые команды не могут быть подготовлены. Например, команды, указывающие выполнение хранимой процедуры или содержащие недопустимый текст для создания хранимой процедуры [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], подготавливаться не должны.  
  
 При создании временной хранимой процедуры поставщик OLE DB для собственного клиента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] выполняет временную хранимую процедуру и возвращает результаты, как если бы выполнялась сама инструкция.  
  
 Создание временных хранимых процедур управляется свойством инициализации SSPROP_INIT_USEPROCFORPREP, определяемым поставщиком OLE DB для собственного клиента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Если свойство имеет значение SSPROPVAL_USEPROCFORPREP_ON или SSPROPVAL_USEPROCFORPREP_ON_DROP, то поставщик OLE DB для собственного клиента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] при подготовке команды выполняет попытку создать хранимую процедуру. Хранимая процедура будет создана успешно, если пользователь приложения имеет все необходимые разрешения [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 Для потребителей, изредка теряющих соединение, создание временных хранимых процедур может потребовать значительных ресурсов **tempdb**, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] системной базы данных, в котором создаются временные объекты. Если свойство SSPROP_INIT_USEPROCFORPREP имеет значение SSPROPVAL_USEPROCFORPREP_ ON, то временные хранимые процедуры, созданные поставщиком OLE DB для собственного клиента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], удаляются только после потери соединения сеанса, создавшего команду, с экземпляром [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Если это соединение по умолчанию, созданное при инициализации источника данных, то временная хранимая процедура удаляется только тогда, когда источник данных становится неинициализированным.  
  
 Если свойство SSPROP_INIT_USEPROCFORPREP имеет значение SSPROPVAL_USEPROCFORPREP_ON_DROP, то временные хранимые процедуры поставщика OLE DB для собственного клиента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] будут удаляться только в следующих случаях.  
  
-   Потребитель вызывает **ICommandText::SetCommandText** для задания новой команды.  
  
-   Потребитель вызывает **ICommandPrepare::Unprepare** для указания, что текст команды больше не требуется.  
  
-   Потребитель освобождает все ссылки на объект команды, связанной с временной хранимой процедурой.  
  
 Объект команды имеет не более одной хранимой процедуры в **tempdb**. Любая существующая временная хранимая процедура представляет текущий текст команды для этого объекта.  
  
## <a name="see-also"></a>См. также:  
 [Команды](../../relational-databases/native-client-ole-db-commands/commands.md)  
  
  
