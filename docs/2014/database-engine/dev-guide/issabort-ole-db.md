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
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2020
ms.locfileid: "62781040"
---
# <a name="issabort-ole-db"></a>ISSAbort (OLE DB)
  Интерфейс **ISSAbort** , доступ к которому обеспечивает поставщик OLE DB собственного клиента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , предоставляет метод [ISSAbort::Abort](../../relational-databases/native-client-ole-db-interfaces/issabort-abort-ole-db.md) , используемый для отмены текущего набора строк, а также любых команд, находящихся в одном пакете с командой, первоначально создавшей этот набор строк, и еще не завершивших выполнение.  
  
 Интерфейс**ISSAbилиt** является специфичным для поставщика собственного клиента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ; доступ к этому интерфейсу можно получить с помощью метода **QueryInterface** интерфейса **IMultipleResults** объекта, возвращенного методом **ICommand::Execute** или **IOpenRowset::OpenRowset**.  
  
## <a name="in-this-section"></a>В этом разделе  
  
|Метод|Описание|  
|------------|-----------------|  
|[ISSAbort:: Abort &#40;OLE DB&#41;](../../relational-databases/native-client-ole-db-interfaces/issabort-abort-ole-db.md)|Отменяет текущий набор строк и любые пакетные команды, ассоциированные с текущей командой.|  
  
## <a name="see-also"></a>См. также  
 [Интерфейсы (OLE DB)](../../../2014/database-engine/dev-guide/interfaces-ole-db.md)  
  
  
