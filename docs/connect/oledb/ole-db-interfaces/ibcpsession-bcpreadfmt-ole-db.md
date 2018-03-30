---
title: Метод IBCPSession::BCPReadFmt (OLE DB) | Документы Microsoft
description: С помощью IBCPSession::BCPReadFmt для чтения данных из файла форматирования (OLE DB)
ms.custom: ''
ms.date: 03/26/2018
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: ''
ms.component: ole-db-interfaces
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IBCPSession::BCPReadFmt (OLE DB)
apitype: COM
helpviewer_keywords:
- BCPReadFmt method
author: pmasl
ms.author: Pedro.Lopes
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: d31ac29c0fc70877042ffacef94b8187c2aa312d
ms.sourcegitcommit: 9f4330a4b067deea396b8567747a6771f35e6eee
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/30/2018
---
# <a name="ibcpsessionbcpreadfmt-ole-db"></a>Метод IBCPSession::BCPReadFmt (OLE DB)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Считывает сведения о формате для каждого столбца из файла форматирования.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
HRESULT BCPReadFmt(   
      const wchar_t *pwszFormatFile);  
```  
  
## <a name="remarks"></a>Замечания  
 Метод **BCPReadFmt** используется для считывания данных из файла форматирования, указывающего формат данных в файле данных. Данный метод способен определить правильную версию файла форматирования. Он может автоматически определить, в каком формате находится файл форматирования — XML или формат текста по старому стилю, —и действовать соответствующим образом. Драйвер OLE DB для SQL Server BCP поддерживает версии файла форматирования имеют версию 6.0 или более поздней версии.  
  
 После **BCPReadFmt** метод считывает значения формата, он выполняет соответствующие вызовы [IBCPSession::BCPColumns](../../oledb/ole-db-interfaces/ibcpsession-bcpcolumns-ole-db.md) и [IBCPSession::BCPColFmt](../../oledb/ole-db-interfaces/ibcpsession-bcpcolfmt-ole-db.md) методы. Пользователю не требуется производить анализ файла форматирования и выполнять эти вызовы.  
  
 Чтобы сохранить файл форматирования, вызовите [IBCPSession::BCPWriteFmt](../../oledb/ole-db-interfaces/ibcpsession-bcpwritefmt-ole-db.md) метод. Вызовы метода **BCPReadFmt** могут ссылаться на сохраненные форматы. Кроме того, программа массового копирования (**bcp**) может сохранять определяемые пользователем форматы данных в файлах, на которые может ссылаться метод **BCPReadFmt** .  
  
 **BCP_OPTION_DELAYREADFMT** значение *eOption* параметр [IBCPSession::BCPControl](../../oledb/ole-db-interfaces/ibcpsession-bcpcontrol-ole-db.md) изменяет поведение IBCPSession::BCPReadFmt.  
  
## <a name="arguments"></a>Аргументы  
 *pwszFormatFile*[in]  
 Путь и имя файла, содержащего значения формата для файла данных.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 S_OK  
 Метод выполнен успешно.  
  
 E_FAIL  
 Произошла ошибка поставщика, для использования подробных сведений [ISQLServerErrorInfo](http://msdn.microsoft.com/library/a8323b5c-686a-4235-a8d2-bda43617b3a1) интерфейса.  
  
 E_OUTOFMEMORY  
 Ошибка, связанная с нехваткой памяти.  
  
 E_UNEXPECTED  
 Непредвиденный вызов метода. Например [IBCPSession::BCPInit](../../oledb/ole-db-interfaces/ibcpsession-bcpinit-ole-db.md) перед вызовом этого метода не был вызван метод.  
  
## <a name="see-also"></a>См. также  
 [IBCPSession &#40;OLE DB&#41;](../../oledb/ole-db-interfaces/ibcpsession-ole-db.md)   
 [Выполнение операций массового копирования](../../oledb/features/performing-bulk-copy-operations.md)  
  
  
