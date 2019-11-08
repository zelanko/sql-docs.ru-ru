---
title: 'IBCPSession:: BCPColumns (OLE DB) | Документация Майкрософт'
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
apiname:
- IBCPSession::BCPColumns (OLE DB)
apitype: COM
helpviewer_keywords:
- BCPColumns method
ms.assetid: c338abe8-9e30-4853-a7c6-b1a6c00095e1
author: MightyPen
ms.author: genemi
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 1b5385d32ef349284f261a457391581b6e28da03
ms.sourcegitcommit: 856e42f7d5125d094fa84390bc43048808276b57
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/07/2019
ms.locfileid: "73789703"
---
# <a name="ibcpsessionbcpcolumns-ole-db"></a>IBCPSession::BCPColumns (OLE DB)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Задает количество полей для привязки к столбцам в таблице [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
HRESULT BCPColumns(   
      DBCOUNTITEM nColumns);  
```  
  
## <a name="remarks"></a>Замечания  
 Этот метод совершает внутренний вызов метода [IBCPSession::BCPColFmt](../../relational-databases/native-client-ole-db-interfaces/ibcpsession-bcpcolfmt-ole-db.md) для установки значений по умолчанию для полей данных. Эти значения по умолчанию получаются из информации о столбце SQL Server, которую внутренним образом возвращает поставщик, когда имя таблицы указывается через [IBCPSession::BCPInit](../../relational-databases/native-client-ole-db-interfaces/ibcpsession-bcpinit-ole-db.md).  
  
> [!NOTE]  
>  Данный метод можно вызывать только после того, как вызван метод **BCPInit** с допустимым именем файла.  
  
 Этот метод следует вызывать только в случае, когда планируется использовать нестандартный формат пользовательского файла. Дополнительную информацию об описании стандартного формата пользовательского файла см. в справке по методу **BCPInit** .  
  
 После вызова метода **BCPColumns** следует вызвать метод **BCPColFmt** для каждого столбца в пользовательском файле, чтобы полностью описать нестандартный формат файла.  
  
## <a name="arguments"></a>Аргументы  
 *nColumns*[in]  
 Общее число полей в пользовательском файле. Даже если предполагается массовое копирование данных из пользовательского файла в таблицу SQL Server и не предполагается копирование всех полей в пользовательском файле, аргументу *nColumns* следует присвоить значение, равное общему числу полей в пользовательском файле. Затем с помощью свойства **BCPColFmt**можно указать поля, которые нужно пропустить.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 S_OK  
 Метод выполнен успешно.  
  
 E_FAIL  
 Произошла ошибка, связанная с поставщиком. Подробные сведения можно получить при помощи интерфейса [ISQLServerErrorInfo](https://msdn.microsoft.com/library/a8323b5c-686a-4235-a8d2-bda43617b3a1).  
  
 E_UNEXPECTED  
 Непредвиденный вызов метода. Например, перед вызовом этого метода не был вызван метод **BCPInit** . Это значение возвращается также, если данный метод был вызван несколько раз для операции массового копирования.  
  
 E_OUTOFMEMORY  
 Недостаточно памяти.  
  
## <a name="see-also"></a>См. также раздел  
 [IBCPSession &#40;OLE DB&#41; ](../../relational-databases/native-client-ole-db-interfaces/ibcpsession-ole-db.md)   
 [Выполнение операций массового копирования](../../relational-databases/native-client/features/performing-bulk-copy-operations.md)  
  
  
