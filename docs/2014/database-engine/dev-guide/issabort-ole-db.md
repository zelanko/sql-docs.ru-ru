---
title: ISSAbort (OLE DB) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: reference
topic_type:
- apiref
helpviewer_keywords:
- ISSAbort interface
ms.assetid: 7c4df482-4a83-4da0-802b-3637b507693a
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 801eb84df08837ec8e49b6bb0e28fc1f1115e674
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "62781040"
---
# <a name="issabort-ole-db"></a>ISSAbort (OLE DB)
  Интерфейс **ISSAbort** , доступ к которому обеспечивает поставщик OLE DB собственного клиента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , предоставляет метод [ISSAbort::Abort](../../relational-databases/native-client-ole-db-interfaces/issabort-abort-ole-db.md) , используемый для отмены текущего набора строк, а также любых команд, находящихся в одном пакете с командой, первоначально создавшей этот набор строк, и еще не завершивших выполнение.  
  
 **ISSAbort** — это [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] интерфейс, зависящий от поставщика собственного клиента, доступный с помощью **QueryInterface** в объекте **IMultipleResults** , возвращаемом методом **ICommand:: Execute** или **IOpenRowset:: OPENROWSET**.  
  
## <a name="in-this-section"></a>в этом разделе  
  
|Метод|Description|  
|------------|-----------------|  
|[ISSAbort:: Abort &#40;OLE DB&#41;](../../relational-databases/native-client-ole-db-interfaces/issabort-abort-ole-db.md)|Отменяет текущий набор строк и любые пакетные команды, ассоциированные с текущей командой.|  
  
## <a name="see-also"></a>См. также:  
 [Интерфейсы &#40;OLE DB&#41;](../../../2014/database-engine/dev-guide/interfaces-ole-db.md)  
  
  
