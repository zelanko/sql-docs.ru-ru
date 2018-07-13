---
title: ISSAbort (OLE DB) | Документация Майкрософт
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
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 6ace6518c1a0f4ece66ec0b9b24cb9e109db7ffa
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37180351"
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
  
  
