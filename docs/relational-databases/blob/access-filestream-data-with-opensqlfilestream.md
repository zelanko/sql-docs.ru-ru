---
title: "Доступ к данным FILESTREAM с помощью OpenSqlFilestream | Документация Майкрософт"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- dbe-blob
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- OpenSqlFilestream
apilocation:
- sqlncli11.dll
apitype: DLLExport
helpviewer_keywords:
- OpenSqlFilestream
ms.assetid: d8205653-93dd-4599-8cdf-f9199074025f
caps.latest.revision: 47
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 6ce631c94bbc15ab1df2450a089c773a960b1401
ms.contentlocale: ru-ru
ms.lasthandoff: 04/11/2017

---
# <a name="access-filestream-data-with-opensqlfilestream"></a>Доступ к данным FILESTREAM с OpenSqlFilestream
  API OpenSqlFilestream получает дескриптор файла, совместимый с Win32, для большого двоичного объекта FILESTREAM, хранящегося в файловой системе. Дескриптор может быть передан в любой из следующих API-интерфейсов Win32: [ReadFile](http://go.microsoft.com/fwlink/?LinkId=86422), [WriteFile](http://go.microsoft.com/fwlink/?LinkId=86423), [TransmitFile](http://go.microsoft.com/fwlink/?LinkId=86424), [SetFilePointer](http://go.microsoft.com/fwlink/?LinkId=86425), [SetEndOfFile](http://go.microsoft.com/fwlink/?LinkId=86426)или [FlushFileBuffers](http://go.microsoft.com/fwlink/?LinkId=86427). При передаче этого дескриптора любому другому API Win32 будет возвращена ошибка ERROR_ACCESS_DENIED. Дескриптор следует закрыть, передав его API-интерфейсу Win32 [CloseHandle](http://go.microsoft.com/fwlink/?LinkId=86428) перед фиксацией или откатом транзакции. Если дескриптор не будет закрыт, то это вызовет утечку ресурсов со стороны сервера.  
  
 Весь доступ к контейнеру данных FILESTREAM осуществляется в транзакции [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . [!INCLUDE[tsql](../../includes/tsql-md.md)] могут выполняться в ней же. Это обеспечивает согласованность данных SQL и данных FILESTREAM BLOB.  
  
 Чтобы получить доступ к объекту FILESTREAM BLOB с помощью Win32, необходимо включить [авторизацию Windows](../../relational-databases/security/choose-an-authentication-mode.md) .  
  
> [!IMPORTANT]  
>  Если открывается доступ к файлу для записи, то транзакция принадлежит агенту FILESTREAM. Пока транзакция не будет разблокирована, возможен только файловый ввод-вывод Win32. Для освобождении транзакции дескриптор записи должен быть закрыт.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
HANDLE OpenSqlFilestream (  
    LPCWSTR FilestreamPath,  
    SQL_FILESTREAM_DESIRED_ACCESS DesiredAccess,  
    ULONG OpenOptions,  
    LPBYTE FilestreamTransactionContext,  
    SIZE_T FilestreamTransactionContextLength,  
    PLARGE_INTEGER AllocationSize);  
```  
  
#### <a name="parameters"></a>Параметры  
 *FilestreamPath*  
 [входящее значение] Путь типа **nvarchar(max)** , который возвращается функцией [PathName](../../relational-databases/system-functions/pathname-transact-sql.md) . PathName можно вызывать только из контекста учетной записи, которая имеет разрешения SELECT или UPDATE [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] для таблицы FILESTREAM и столбца.  
  
 *DesiredAccess*  
 [in] Задает режим, используемый при доступе к данным FILESTREAM BLOB. Это значение передается функции [DeviceIoControl Function](http://go.microsoft.com/fwlink/?LinkId=105527).  
  
|Название|Значение|Значение|  
|----------|-----------|-------------|  
|SQL_FILESTREAM_READ|0|Данные могут быть считаны из файла.|  
|SQL_FILESTREAM_WRITE|1|Данные могут быть записаны в файл.|  
|SQL_FILESTREAM_READWRITE|2|Данные могут быть считаны из файла и записаны в него.|  
  
> [!NOTE]  
>  Эти значения определяются в перечислении SQL_FILESTREAM_DESIRED_ACCESS, расположенном в файле sqlncli.h.  
  
 *OpenOptions*  
 [in] Атрибуты и флаги файла. В этот параметр может входить любое сочетание следующих флагов.  
  
|Флаг|Значение|Значение|  
|----------|-----------|-------------|  
|SQL_FILESTREAM_OPEN_NONE|0x00000000L|Файл открывается или создается без специальных параметров.|  
|SQL_FILESTREAM_OPEN_FLAG_ASYNC|0x00000001L|Файл открывается или создается для асинхронного ввода-вывода.|  
|SQL_FILESTREAM_OPEN_FLAG_NO_BUFFERING|0x00000002L|Система открывает файл, не используя системное кэширование.|  
|SQL_FILESTREAM_OPEN_FLAG_NO_WRITE_THROUGH|0x00000004L|Система не записывает данные в промежуточный кэш. Запись производится непосредственно на диск.|  
|SQL_FILESTREAM_OPEN_FLAG_SEQUENTIAL_SCAN|0x00000008L|Доступ к файлу осуществляется последовательно от начала до конца. Система может использовать это в качестве указания для оптимизации кэширования файлов. Если приложение перемещает указатель файла для случайного доступа, кэширование может произойти неоптимально.|  
|SQL_FILESTREAM_OPEN_FLAG_RANDOM_ACCESS|0x00000010L|Доступ к файлу осуществляется случайным образом. Система может использовать это в качестве указания для оптимизации кэширования файлов.|  
  
 *FilestreamTransactionContext*  
 [входящее значение] Значение, возвращаемое функцией [GET_FILESTREAM_TRANSACTION_CONTEXT](../../t-sql/functions/get-filestream-transaction-context-transact-sql.md) .  
  
 *FilestreamTransactionContextLength*  
 [входящее значение] Число байтов в данных типа **varbinary(max)** , возвращаемых функцией GET_FILESTREAM_TRANSACTION_CONTEXT. Функция возвращает массив из N байт. Число N определяется функцией и является свойством возвращаемого массива байт.  
  
 *AllocationSize*  
 [in] Указывает изначально выделяемый размер файла данных в байтах. Не учитывается в режиме чтения. Этот параметр может иметь значение NULL, в этом случае используется поведение файловой системы по умолчанию.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Если функция завершается успешно, возвращается открытый дескриптор на указанный файл. Если функция завершается неудачно, возвращается значение INVALID_HANDLE_VALUE. Дополнительные сведения об ошибке можно получить с помощью функции GetLastError().  
  
## <a name="examples"></a>Примеры  
 В следующих примерах показано, как можно использовать функцию API `OpenSqlFilestream` для получения дескриптора Win32.  
  
 [!code-cs[FILESTREAM#FS_CS_ReadAndWriteBLOB](../../relational-databases/blob/codesnippet/csharp/access-filestream-data-w_0_1.cs)]  
  
 [!code-vb[FILESTREAM#FS_VB_ReadAndWriteBLOB](../../relational-databases/blob/codesnippet/visualbasic/access-filestream-data-w_0_2.vb)]  
  
 [!code-cpp[FILESTREAM#FS_CPP_WriteBLOB](../../relational-databases/blob/codesnippet/cpp/access-filestream-data-w_0_3.cpp)]  
  
## <a name="remarks"></a>Замечания  
 Чтобы использовать эту функцию API, должен быть установлен собственный клиент [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Клиент [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client устанавливается совместно с клиентскими средствами [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] или [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Дополнительные сведения см. в статье [Установка SQL Server Native Client](../../relational-databases/native-client/applications/installing-sql-server-native-client.md).  
  
## <a name="see-also"></a>См. также:  
 [Большой двоичный объект &#40;BLOB-объект&#41;Данные&#40;SQL Server&#41;](../../relational-databases/blob/binary-large-object-blob-data-sql-server.md)   
 [Создание частичных обновлений данных FILESTREAM](../../relational-databases/blob/make-partial-updates-to-filestream-data.md)   
 [Избегание конфликтов в операциях баз данных в приложениях FILESTREAM](../../relational-databases/blob/avoid-conflicts-with-database-operations-in-filestream-applications.md)  
  
  
