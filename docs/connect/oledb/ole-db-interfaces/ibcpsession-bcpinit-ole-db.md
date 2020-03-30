---
title: IBCPSession::BCPInit (OLE DB) | Документация Майкрософт
description: IBCPSession::BCPInit (OLE DB)
ms.custom: ''
ms.date: 06/14/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: connectivity
ms.topic: reference
apiname:
- IBCPSession::BCPInit (OLE DB)
apitype: COM
helpviewer_keywords:
- BCPInit method
author: pmasl
ms.author: pelopes
ms.openlocfilehash: 02a05f99919bbd35b1064d14c82dec9fba6cee78
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/29/2020
ms.locfileid: "67994565"
---
# <a name="ibcpsessionbcpinit-ole-db"></a>IBCPSession::BCPInit (OLE DB)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  Инициализирует структуру массового копирования, выполняет проверку ошибок, проверяет правильность имен файла данных и файла форматирования, а затем открывает эти файлы.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
HRESULT BCPInit(   
      const wchar_t *pwszTable,  
      const wchar_t *pwszDataFile,  
      const wchar_t *pwszErrorFile,  
      int eDirection);  
```  
  
## <a name="remarks"></a>Remarks  
 Метод **BCPInit** необходимо вызывать перед вызовом любого другого метода массового копирования. Метод **BCPInit** выполняет необходимые инициализации для массового копирования данных между рабочей станцией и [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
 Метод **BCPInit** проверяет структуру конечной или исходной таблицы базы данных, а не файл данных. Он указывает значения форматов данных для файла данных на основе каждого столбца в таблице, представлении базы данных или результирующем наборе SELECT. Эта спецификация включает тип данных каждого столбца, присутствие или отсутствие длины и допустимости значений NULL и строки байтов признака конца, а также ширину для типов данных с фиксированной длиной. Метод **BCPInit** устанавливает эти значения указанным ниже образом.  
  
-   Указанный тип данных представляет собой тип данных столбца в таблице базы данных, представлении или результирующем наборе SELECT. Тип данных перечислен в собственных типах данных [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], которые указываются в файле заголовка OLE DB Driver for SQL Server (msoledbsql.h). Их значения строятся по следующему шаблону: BCP_TYPE_XXX. Данные представлены в компьютерной форме. Это значит, что данные из столбца с типом данных integer представлены четырехбайтовой последовательностью с прямым или обратным порядком следования байтов в зависимости от компьютера, создавшего файл данных.  
  
-   Если тип данных базы данных имеет фиксированную длину, то для данных файла данных также задается фиксированная длина. Методы массового копирования, обрабатывающие данные (например, [IBCPSession::BCPExec](../../oledb/ole-db-interfaces/ibcpsession-bcpexec-ole-db.md)) анализируют строки данных, ожидая, что длина данных в файле данных будет совпадать с длиной данных, определенной в таблице или представлении базы данных или списке столбцов SELECT. Например, данные в столбце базы данных, определенные как `char(13)`, должны быть представлены в виде 13 символов для каждой строки данных в файле. Данные фиксированной длины могут быть обозначены префиксом с признаком значения NULL, если столбец базы данных допускает значения NULL.  
  
-   При копировании данных в [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] файл данных должен содержать данные для каждого столбца в таблице базы данных. При копировании данных из [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] данные из всех столбцов таблицы, представления или результирующего набора SELECT базы данных копируются в файл данных.  
  
-   При копировании данных в [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] порядковый номер столбца в файле данных должен совпадать с порядковым номером столбца в таблице базы данных. При копировании из [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] метод **BCPExec** размещает данные, исходя из порядкового номера столбца в таблице базы данных.  
  
-   Если тип данных в базе данных является типом с переменной длиной (например, `varbinary(22)`), или если столбец базы данных может содержать значения NULL, данные в файле данных предваряются признаком длины и допустимости значений NULL. Ширина признака изменяется в зависимости от типа данных и версии массового копирования. Параметр BCP_OPTION_FILEFMT метода [IBCPSession::BCPControl](../../oledb/ole-db-interfaces/ibcpsession-bcpcontrol-ole-db.md) обеспечивает совместимость между более ранними файлами данных для массового копирования и серверами с более новыми версиями [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], указывая, когда ширина признаков в данных меньше, чем ожидаемая.  
  
> [!NOTE]  
>  Чтобы изменить значения форматов данных, указанные для файла данных, используйте методы [IBCPSession::BCPColumns](../../oledb/ole-db-interfaces/ibcpsession-bcpcolumns-ole-db.md) и [IBCPSession::BCPColFmt](../../oledb/ole-db-interfaces/ibcpsession-bcpcolfmt-ole-db.md).  
  
 Для таблиц, не содержащих индексы, можно оптимизировать массовое копирование в [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], установив параметр базы данных **select into/bulkcopy**.  
  
## <a name="arguments"></a>Аргументы  
 *pwszTable*[IN]  
 Имя таблицы базы данных, в которую или из которой выполняется копирование. Имя может включать имя базы данных или имя владельца. Примеры: «pubs.username.titles», «pubs..titles», «username.titles».  
  
 Если аргумент eDirection имеет значение BCP_DIRECTION_OUT, аргумент pwszTable может являться именем представления базы данных.  
  
 Если аргумент eDirection имеет значение BCP_DIRECTION_OUT и инструкция SELECT указана с помощью метода **BCPControl** перед вызовом метода **BCPExec**, аргумент *pwszTable* должен иметь значение NULL.  
  
 *pwszDataFile*[IN]  
 Имя пользовательского файла, в который или из которого выполняется копирование.  
  
 *pwszErrorFile*[IN]  
 Имя файла ошибок, который заполняется сообщениями о ходе выполнения, сообщениями об ошибках и копиями строк, которые не удалось скопировать из пользовательского файла в таблицу. Если аргумент *pwszErrorFile* имеет значение NULL, файл ошибок не используется.  
  
 *eDirection*[IN]  
 Направление операции копирования: BCP_DIRECTION_IN или BCP_DIRECTION _OUT. BCP_DIRECTION _IN обозначает копирование из пользовательского файла в таблицу базы данных; BCP_DIRECTION _OUT обозначает копирование из таблицы базы данных в пользовательский файл.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 S_OK  
 Метод выполнен успешно.  
  
 E_FAIL  
 Произошла ошибка, связанная с поставщиком. Подробные сведения можно получить с помощью интерфейса [ISQLServerErrorInfo](https://msdn.microsoft.com/library/a8323b5c-686a-4235-a8d2-bda43617b3a1).  
  
 E_OUTOFMEMORY  
 Недостаточно памяти.  
  
 E_INVALIDARG  
 Один или несколько аргументов были указаны неправильно. Например, указано недопустимое имя файла.  
  
## <a name="see-also"></a>См. также:  
 [IBCPSession &#40;OLE DB&#41;](../../oledb/ole-db-interfaces/ibcpsession-ole-db.md)   
 [Выполнение операций массового копирования](../../oledb/features/performing-bulk-copy-operations.md)  
  
  
