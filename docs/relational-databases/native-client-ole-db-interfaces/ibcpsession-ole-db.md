---
title: IBCPSession (OLE DB) | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
apitype: COM
helpviewer_keywords:
- IBCPSession interface
ms.assetid: 00d0311f-8b71-4ad6-824d-0e89119347a3
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 653bd8aad3a10a3929b7ced76e28e4d570733ad3
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81307355"
---
# <a name="ibcpsession-ole-db"></a>Интерфейс IBCPSession (OLE DB)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Интерфейс **IBCPSession** предоставляет поддержку операций массового копирования [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] на основе файлов. Интерфейс **IBCPSession** представлен в поставщике OLE DB собственного клиента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] под тем же уровнем, что и объекты Session. В поставщике OLE DB собственного клиента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] объекты источника данных являются фабриками объектов Session, и операции массового копирования указываются в свойстве соединения SSPROP_ENABLEBULKCOPY. Кроме того, свойство SSPROP_ENABLEFASTLOAD должно быть установлено в значение TRUE.  
  
 Вызов метода **IDBCreateSession::CreateSession** приведет к созданию объекта **BulkCopySession** . Все методы массового копирования, основанные на файлах, доступные через объект **IBCPSession** , можно вызывать с помощью этих объектов **IBCPSession** интерфейса **IBCPSession** .  
  
> [!NOTE]  
>  Поставщик OLE DB собственного клиента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поддерживает операции массового копирования в памяти через интерфейс [IRowsetFastLoad](../../relational-databases/native-client-ole-db-interfaces/irowsetfastload-ole-db.md) .  
  
 Для получения дополнительной [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] информации об использовании поставщика Native Client OLE DB для операций с объемом копирования см. [Performing Bulk Copy Operations](../../relational-databases/native-client/features/performing-bulk-copy-operations.md)  
  
 Пример использования интерфейса **IBCPSession** см. в статье [IBCPSession::BCPDone &#40;OLE DB&#41;](../../relational-databases/native-client-ole-db-interfaces/ibcpsession-bcpdone-ole-db.md).  
  
## <a name="in-this-section"></a>в этом разделе  
  
|Метод|Описание|  
|------------|-----------------|  
|[IBCPSession::BCPColFmt &#40;OLE DB&#41;](../../relational-databases/native-client-ole-db-interfaces/ibcpsession-bcpcolfmt-ole-db.md)|Создает привязку между переменными программы и столбцами [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .|  
|[IBCPSession::BCPColumns &#40;OLE DB&#41;](../../relational-databases/native-client-ole-db-interfaces/ibcpsession-bcpcolumns-ole-db.md)|Задает количество полей для привязки к столбцам в таблице [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .|  
|[IBCPSession::BCPControl &#40;OLE DB&#41;](../../relational-databases/native-client-ole-db-interfaces/ibcpsession-bcpcontrol-ole-db.md)|Устанавливает параметры для операции массового копирования.|  
|[IBCPSession::BCPDone &#40;OLE DB&#41;](../../relational-databases/native-client-ole-db-interfaces/ibcpsession-bcpdone-ole-db.md)|Фиксирует оставшиеся строки для отправки в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|[IBCPSession::BCPExec &#40;OLE DB&#41;](../../relational-databases/native-client-ole-db-interfaces/ibcpsession-bcpexec-ole-db.md)|Выполняет операцию массового копирования.|  
|[IBCPSession::BCPInit &#40;OLE DB&#41;](../../relational-databases/native-client-ole-db-interfaces/ibcpsession-bcpinit-ole-db.md)|Инициализирует структуру массового копирования, выполняет проверку ошибок, проверяет правильность имен файла данных и файла форматирования, а затем открывает эти файлы.|  
|[IBCPSession::BCPReadFmt &#40;OLE DB&#41;](../../relational-databases/native-client-ole-db-interfaces/ibcpsession-bcpreadfmt-ole-db.md)|Считывает сведения о формате для каждого столбца из файла форматирования.|  
|[IBCPSession::BCPWriteFmt &#40;OLE DB&#41;](../../relational-databases/native-client-ole-db-interfaces/ibcpsession-bcpwritefmt-ole-db.md)|Записывает в файл форматирования сведения о формате каждого из столбцов.|  
  
## <a name="see-also"></a>См. также:  
 [Интерфейсы (OLE DB)](https://msdn.microsoft.com/library/34c33364-8538-45db-ae41-5654481cda93)  
  
  
