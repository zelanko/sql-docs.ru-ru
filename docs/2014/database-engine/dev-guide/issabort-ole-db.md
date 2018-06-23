---
title: ISSAbort (OLE DB) | Документы Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
topic_type:
- apiref
helpviewer_keywords:
- ISSAbort interface
ms.assetid: 7c4df482-4a83-4da0-802b-3637b507693a
caps.latest.revision: 11
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 53c6e2c7c06331ce75883f86a8935d4d1c2419c4
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36098459"
---
# <a name="issabort-ole-db"></a>ISSAbort (OLE DB)
  **ISSAbort** интерфейс, который предоставляется в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поставщик OLE DB для собственного клиента предоставляет [ISSAbort::Abort](../../relational-databases/native-client-ole-db-interfaces/issabort-abort-ole-db.md) метод, используемый для отмены текущего набора строк, а также все команды в пакетном режиме с командой, первоначально создавшей набор строк, и который еще не завершивших выполнение.  
  
 **ISSAbort** — [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] интерфейс поставщика собственного клиента, доступный с помощью **QueryInterface** на **IMultipleResults** объект, возвращаемый  **ICommand::Execute** или **IOpenRowset::OpenRowset**.  
  
## <a name="in-this-section"></a>в этом разделе  
  
|Метод|Описание|  
|------------|-----------------|  
|[ISSAbort::Abort &#40;OLE DB&#41;](../../relational-databases/native-client-ole-db-interfaces/issabort-abort-ole-db.md)|Отменяет текущий набор строк и любые пакетные команды, ассоциированные с текущей командой.|  
  
## <a name="see-also"></a>См. также  
 [Интерфейсы &#40;OLE DB&#41;](../../../2014/database-engine/dev-guide/interfaces-ole-db.md)  
  
  