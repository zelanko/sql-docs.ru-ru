---
title: 'IBCPSession:: BCPWriteFmt (OLE DB) | Документация Майкрософт'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
apiname:
- IBCPSession::BCPWriteFmt (OLE DB)
apitype: COM
helpviewer_keywords:
- BCPWriteFmt method
ms.assetid: add50425-2ed6-411a-a391-4ce63c364892
author: MightyPen
ms.author: genemi
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: be81642fc0ce903e51c1ecc7c6e322125765569f
ms.sourcegitcommit: 856e42f7d5125d094fa84390bc43048808276b57
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/07/2019
ms.locfileid: "73763808"
---
# <a name="ibcpsessionbcpwritefmt-ole-db"></a>IBCPSession::BCPWriteFmt (OLE DB)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Записывает в файл форматирования сведения о формате каждого из столбцов.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
HRESULT BCPWriteFmt(   
      const wchar_t *pwszFormatFile);  
```  
  
## <a name="remarks"></a>Замечания  
 Файл форматирования определяет формат данных, содержащихся в файле данных, создаваемом при массовом копировании. Вызовы методов [IBCPSession::BCPColumns](../../relational-databases/native-client-ole-db-interfaces/ibcpsession-bcpcolumns-ole-db.md) и [IBCPSession::BCPColFmt](../../relational-databases/native-client-ole-db-interfaces/ibcpsession-bcpcolfmt-ole-db.md) определяют формат файла данных. Метод **BCPWriteFmt** сохраняет это определение в файле, на который ссылается аргумент pwszFormatFile.  
  
 Метод **BCPWriteFmt** может сохранять файлы форматирования в формате xml или текстовом формате. Это должно определяться при помощи параметра управления BCP_OPTION_XML методом [IBCPSession::BCPControl](../../relational-databases/native-client-ole-db-interfaces/ibcpsession-bcpcontrol-ole-db.md) .  
  
 Для загрузки сохраненного файла форматирования используется метод [IBCPSession::BCPReadFmt](../../relational-databases/native-client-ole-db-interfaces/ibcpsession-bcpreadfmt-ole-db.md) .  
  
## <a name="arguments"></a>Аргументы  
 *pwszFormatFile*[in]  
 Путь и имя файла, содержащего значения формата для файла данных.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 S_OK  
 Метод выполнен успешно.  
  
 E_FAIL  
 Произошла ошибка, связанная с поставщиком. Подробные сведения можно получить при помощи интерфейса [ISQLServerErrorInfo](https://msdn.microsoft.com/library/a8323b5c-686a-4235-a8d2-bda43617b3a1).  
  
 E_OUTOFMEMORY  
 Недостаточно памяти.  
  
 E_UNEXPECTED  
 Непредвиденный вызов метода. Например, перед вызовом этого метода не был вызван метод [IBCPSession::BCPInit](../../relational-databases/native-client-ole-db-interfaces/ibcpsession-bcpinit-ole-db.md) .  
  
## <a name="see-also"></a>См. также раздел  
 [IBCPSession &#40;OLE DB&#41; ](../../relational-databases/native-client-ole-db-interfaces/ibcpsession-ole-db.md)   
 [Выполнение операций массового копирования](../../relational-databases/native-client/features/performing-bulk-copy-operations.md)  
  
  
