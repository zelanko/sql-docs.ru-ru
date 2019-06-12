---
title: IBCPSession::BCPExec (OLE DB) | Документация Майкрософт
description: IBCPSession::BCPExec (OLE DB)
ms.custom: ''
ms.date: 06/14/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: connectivity
ms.topic: reference
apiname:
- IBCPSession::BCPExec (OLE DB)
apitype: COM
helpviewer_keywords:
- BCPExec method
author: pmasl
ms.author: pelopes
manager: jroth
ms.openlocfilehash: 087987f64cf3da6e7f14b30c6014fdcd6e35e243
ms.sourcegitcommit: ad2e98972a0e739c0fd2038ef4a030265f0ee788
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 06/07/2019
ms.locfileid: "66790983"
---
# <a name="ibcpsessionbcpexec-ole-db"></a>IBCPSession::BCPExec (OLE DB)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  Выполняет операцию массового копирования.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
HRESULT BCPExec(   
      DBROWCOUNT *pRowsCopied);  
```  
  
## <a name="remarks"></a>Remarks  
 Метод **BCPExec** копирует данные из пользовательского файла в таблицу базы данных или наоборот, в зависимости от значения параметра *eDirection*, используемого в методе [IBCPSession::BCPInit](../../oledb/ole-db-interfaces/ibcpsession-bcpinit-ole-db.md).  
  
 Перед вызовом **BCPExec**вызовите метод **BCPInit** , передав ему допустимое имя файла пользователя. Несоблюдение этого правила приведет к ошибке. Единственное исключение — использование запроса для операции массового копирования из базы данных. В этом случае указывается имя таблицы NULL в методе **BCPInit** , а затем задается запрос, использующий параметр BCP_OPTION_HINTS.  
  
 Метод **BCPExec** — единственный метод массового копирования, который с большой вероятностью может ожидать выполнения в течение любого периода времени. Таким образом, это единственный метод массового копирования, который поддерживает асинхронный режим. Для использования асинхронного режима задайте значение VARIANT_TRUE для свойства сеанса поставщика SSPROP_ASYNCH_BULKCOPY перед вызовом метода **BCPExec** . Это свойство доступно в наборе свойств DBPROPSET_SQLSERVERSESSION. Чтобы проверить завершение операции, вызовите метод **BCPExec** с теми же параметрами. Если массовое копирование еще не завершено, метод **BCPExec** возвращает DB_S_ASYNCHRONOUS. Он также возвращает в аргументе *pRowsCopied* состояние счетчика строк, переданных на сервер или полученных от него. Строки, отправленные на сервер, не фиксируются до тех пор, пока не будет достигнут конец пакета.  
  
## <a name="arguments"></a>Аргументы  
 *pRowsCopied*[out]  
 Указатель на значение типа DWORD. Метод **BCPExec** записывает в значение DWORD количество успешно скопированных строк. Если для аргумента *pRowsCopied* задано значение NULL, то он пропускается методом **BCPExec** .  
  
## <a name="return-code-values"></a>Значения кода возврата  
 S_OK  
 Метод выполнен успешно.  
  
 E_FAIL  
 Произошла ошибка, связанная с поставщиком. Подробные сведения можно получить при помощи интерфейса [ISQLServerErrorInfo](https://msdn.microsoft.com/library/a8323b5c-686a-4235-a8d2-bda43617b3a1) .  
  
 E_UNEXPECTED  
 Непредвиденный вызов метода. Например, перед вызовом этого метода не был вызван метод **BCPInit** . Также возникает, если операция была прервана с использованием параметра BCP_OPTION_ABORT, а затем был вызван метод **BCPExec** .  
  
 E_OUTOFMEMORY  
 Недостаточно памяти.  
  
 DB_S_ENDOFROWSET  
 Операция массового копирования завершена, и вся передача всех данных выполнена.  
  
 DB_S_ASYNCHRONOUS  
 Текущий пакет строк скопирован. Вновь вызовите метод **BCPExec** , чтобы передать следующий пакет.  
  
 DB_S_ERRORSOCCURRED  
 Во время операции массового копирования произошли ошибки, и некоторые строки могли быть не скопированы. Количество ошибок все еще меньше минимально допустимого числа ошибок.  
  
## <a name="see-also"></a>См. также:  
 [IBCPSession &#40;OLE DB&#41;](../../oledb/ole-db-interfaces/ibcpsession-ole-db.md)   
 [Выполнение операций массового копирования](../../oledb/features/performing-bulk-copy-operations.md)  
  
  
