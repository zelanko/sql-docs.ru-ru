---
title: IBCPSession::BCPReadFmt (OLE DB) | Документация Майкрософт
description: С помощью IBCPSession::BCPReadFmt для чтения данных из файла форматирования (OLE DB)
ms.custom: ''
ms.date: 06/14/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: reference
apiname:
- IBCPSession::BCPReadFmt (OLE DB)
apitype: COM
helpviewer_keywords:
- BCPReadFmt method
author: pmasl
ms.author: pelopes
manager: craigg
ms.openlocfilehash: e3e1ee36165308235f1fbe3e3779253655483237
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47771492"
---
# <a name="ibcpsessionbcpreadfmt-ole-db"></a>Метод IBCPSession::BCPReadFmt (OLE DB)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  Считывает сведения о формате для каждого столбца из файла форматирования.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
HRESULT BCPReadFmt(   
      const wchar_t *pwszFormatFile);  
```  
  
## <a name="remarks"></a>Remarks  
 Метод **BCPReadFmt** используется для считывания данных из файла форматирования, указывающего формат данных в файле данных. Данный метод способен определить правильную версию файла форматирования. Он может автоматически определить, в каком формате находится файл форматирования — XML или формат текста по старому стилю, —и действовать соответствующим образом. Версии файла форматирования, поддерживаемые драйвером OLE DB для SQL Server BCP имеют версию 6.0 или более поздней версии.  
  
 После того как метод **BCPReadFmt** считывает значения формата, он выполняет соответствующие вызовы методов [IBCPSession::BCPColumns](../../oledb/ole-db-interfaces/ibcpsession-bcpcolumns-ole-db.md) и [IBCPSession::BCPColFmt](../../oledb/ole-db-interfaces/ibcpsession-bcpcolfmt-ole-db.md). Пользователю не требуется производить анализ файла форматирования и выполнять эти вызовы.  
  
 Чтобы сохранить файл форматирования, вызовите метод [IBCPSession::BCPWriteFmt](../../oledb/ole-db-interfaces/ibcpsession-bcpwritefmt-ole-db.md). Вызовы метода **BCPReadFmt** могут ссылаться на сохраненные форматы. Кроме того, программа массового копирования (**bcp**) может сохранять определяемые пользователем форматы данных в файлах, на которые может ссылаться метод **BCPReadFmt** .  
  
 **BCP_OPTION_DELAYREADFMT** значение *eOption* параметр [IBCPSession::BCPControl](../../oledb/ole-db-interfaces/ibcpsession-bcpcontrol-ole-db.md) изменяет поведение IBCPSession::BCPReadFmt.  
  
## <a name="arguments"></a>Аргументы  
 *pwszFormatFile*[in]  
 Путь и имя файла, содержащего значения формата для файла данных.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 S_OK  
 Метод выполнен успешно.  
  
 E_FAIL  
 Произошла ошибка, связанная с поставщиком. Подробные сведения можно получить с помощью интерфейса [ISQLServerErrorInfo](http://msdn.microsoft.com/library/a8323b5c-686a-4235-a8d2-bda43617b3a1).  
  
 E_OUTOFMEMORY  
 Ошибка, связанная с нехваткой памяти.  
  
 E_UNEXPECTED  
 Непредвиденный вызов метода. Например, перед вызовом этого метода не был вызван метод [IBCPSession::BCPInit](../../oledb/ole-db-interfaces/ibcpsession-bcpinit-ole-db.md).  
  
## <a name="see-also"></a>См. также:  
 [IBCPSession &#40;OLE DB&#41;](../../oledb/ole-db-interfaces/ibcpsession-ole-db.md)   
 [Выполнение операций массового копирования](../../oledb/features/performing-bulk-copy-operations.md)  
  
  
