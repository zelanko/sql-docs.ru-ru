---
title: 'IBCPSession:: BCPInit (OLE DB) | Документация Майкрософт'
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
apiname:
- IBCPSession::BCPInit (OLE DB)
apitype: COM
helpviewer_keywords:
- BCPInit method
ms.assetid: 583096d7-da34-49be-87fd-31210aac81aa
author: MightyPen
ms.author: genemi
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 99c11795cb51e66b9fc1590351445ffcd14aeb34
ms.sourcegitcommit: 856e42f7d5125d094fa84390bc43048808276b57
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/07/2019
ms.locfileid: "73763558"
---
# <a name="ibcpsessionbcpinit-ole-db"></a>IBCPSession::BCPInit (OLE DB)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

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
 Метод **BCPInit** необходимо вызывать перед вызовом любого другого метода массового копирования. Метод **BCPInit** выполняет необходимые инициализации для массового копирования данных между рабочей станцией и [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 Метод **BCPInit** проверяет структуру конечной или исходной таблицы базы данных, а не файл данных. Он указывает значения форматов данных для файла данных на основе каждого столбца в таблице, представлении базы данных или результирующем наборе SELECT. Эта спецификация включает тип данных каждого столбца, присутствие или отсутствие длины и допустимости значений NULL и строки байтов признака конца, а также ширину для типов данных с фиксированной длиной. Метод **BCPInit** устанавливает эти значения указанным ниже образом.  
  
-   Указанный тип данных представляет собой тип данных столбца в таблице базы данных, представлении или результирующем наборе SELECT. Тип данных перечисляется с помощью [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] собственных типов данных, указанных в файле заголовка собственного клиента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (sqlncli. h). Их значения строятся по следующему шаблону: BCP_TYPE_XXX. Данные представлены в компьютерной форме. Это значит, что данные из столбца с типом данных integer представлены четырехбайтовой последовательностью с прямым или обратным порядком следования байтов в зависимости от компьютера, создавшего файл данных.  
  
-   Если тип данных базы данных имеет фиксированную длину, то для данных файла данных также задается фиксированная длина. Методы массового копирования, обрабатывающие данные (например, [IBCPSession::BCPExec](../../relational-databases/native-client-ole-db-interfaces/ibcpsession-bcpexec-ole-db.md)) анализируют строки данных, ожидая, что длина данных в файле данных будет совпадать с длиной данных, определенной в таблице или представлении базы данных или списке столбцов SELECT. Например, данные в столбце базы данных, определенные как `char(13)`, должны быть представлены в виде 13 символов для каждой строки данных в файле. Данные фиксированной длины могут быть обозначены префиксом с признаком значения NULL, если столбец базы данных допускает значения NULL.  
  
-   При копировании данных в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] файл данных должен содержать данные для каждого столбца в таблице базы данных. При копировании данных из [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] данные из всех столбцов таблицы, представления или результирующего набора SELECT базы данных копируются в файл данных.  
  
-   При копировании данных в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] порядковый номер столбца в файле данных должен совпадать с порядковым номером столбца в таблице базы данных. При копировании из [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] метод **BCPExec** размещает данные, исходя из порядкового номера столбца в таблице базы данных.  
  
-   Если тип данных в базе данных является типом с переменной длиной (например, `varbinary(22)`), или если столбец базы данных может содержать значения NULL, данные в файле данных предваряются признаком длины и допустимости значений NULL. Ширина признака изменяется в зависимости от типа данных и версии массового копирования. Параметр BCP_OPTION_FILEFMT метода [IBCPSession::BCPControl](../../relational-databases/native-client-ole-db-interfaces/ibcpsession-bcpcontrol-ole-db.md) обеспечивает совместимость между более ранними файлами данных для массового копирования и серверами с более новыми версиями [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], указывая, когда ширина признаков в данных меньше, чем ожидаемая.  
  
> [!NOTE]  
>  Чтобы изменить значения форматов данных, указанные для файла данных, используйте методы [IBCPSession::BCPColumns](../../relational-databases/native-client-ole-db-interfaces/ibcpsession-bcpcolumns-ole-db.md) и [IBCPSession::BCPColFmt](../../relational-databases/native-client-ole-db-interfaces/ibcpsession-bcpcolfmt-ole-db.md).  
  
 Для таблиц, не содержащих индексы, можно оптимизировать массовое копирование в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], установив параметр базы данных **select into/bulkcopy**.  
  
## <a name="arguments"></a>Аргументы  
 *пвсзтабле*[in]  
 Имя таблицы базы данных, в которую или из которой выполняется копирование. Имя может включать имя базы данных или имя владельца. Примеры: «pubs.username.titles», «pubs..titles», «username.titles».  
  
 Если аргумент eDirection имеет значение BCP_DIRECTION_OUT, аргумент pwszTable может являться именем представления базы данных.  
  
 Если аргумент eDirection имеет значение BCP_DIRECTION_OUT и инструкция SELECT указана с помощью метода **BCPControl** перед вызовом метода **BCPExec**, аргумент *pwszTable* должен иметь значение NULL.  
  
 *пвсздатафиле*[in]  
 Имя пользовательского файла, в который или из которого выполняется копирование.  
  
 *пвсзеррорфиле*[in]  
 Имя файла ошибок, который заполняется сообщениями о ходе выполнения, сообщениями об ошибках и копиями строк, которые не удалось скопировать из пользовательского файла в таблицу. Если для аргумента *пвсзеррорфиле* ЗАДАНО значение null, файл ошибок не используется.  
  
 *eDirection*[in]  
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
  
## <a name="see-also"></a>См. также статью  
 [IBCPSession &#40;OLE DB&#41; ](../../relational-databases/native-client-ole-db-interfaces/ibcpsession-ole-db.md)   
 [Выполнение операций массового копирования](../../relational-databases/native-client/features/performing-bulk-copy-operations.md)  
  
  
