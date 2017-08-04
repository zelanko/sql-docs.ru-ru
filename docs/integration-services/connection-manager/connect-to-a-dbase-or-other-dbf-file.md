---
title: "Подключиться к файлу dBASE или другим файлам DBF | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- connecting to DBF files
- dBase files
- DBF files
ms.assetid: b0e8c831-9f96-475c-82a4-4f5b02692752
caps.latest.revision: 16
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 2b1ae38e8b7ba0a9e584a80d1c6cacc76938576a
ms.contentlocale: ru-ru
ms.lasthandoff: 08/03/2017

---
# <a name="connect-to-a-dbase-or-other-dbf-file"></a>Подключение к файлу dBASE или другим файлам DBF
  В пакетах служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] можно подключиться к dBASE или другим DBF-файлам базы данных, используя диспетчер соединений OLE DB и выбрав поставщика Microsoft OLE DB для Jet 4.0.  
  
> [!NOTE]  
>  Мастер импорта и экспорта SQL Server в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] не поддерживает импорт и экспорт dBASE-файлов и других DBF-файлов. Для импорта данных из DBF-файлов в базу данных Access или электронную таблицу Excel можно использовать Microsoft Access или Microsoft Excel, а затем применить мастер импорта и экспорта SQL Server.  
  
### <a name="to-configure-a-connection-manager-to-connect-to-a-dbase-or-other-dbf-file"></a>Настройка диспетчера соединений для подключения к dBASE и другим DBF-файлам  
  
1.  Добавьте к пакету новый диспетчер соединений OLE DB. Дополнительные сведения см. в разделе [Add, Delete, or Share a Connection Manager in a Package](http://msdn.microsoft.com/library/6f2ba4ea-10be-4c40-9e80-7efcf6ee9655).  
  
2.  На странице **Соединение** диалогового окна **Диспетчер соединений** выберите "Собственный поставщик OLE DB\Поставщик OLE DB для Microsoft Jet 4.0" в поле **Поставщик**.  
  
3.  При работе с DBF-файлами эта папка представляет базу данных, а отдельные DBF-файлы представляют таблицы. Поэтому текстовое поле **Имя файла базы данных** должно содержать путь к папке, в которой находятся DBF-файлы, и включать само имя. Путь к папке можно ввести или вставить либо воспользоваться кнопкой **Обзор** для выбора DBF-файла, а затем удалить имя файла из пути к папке.  
  
4.  На странице **Все** диалогового окна **Диспетчер соединений** введите **dBASE III**, **dBASE IV**или **dBASE 5.0**в качестве значения "Расширенные свойства".  
  
5.  Нажмите кнопку **Проверить соединение** , чтобы проверить введенные значения. Должно появиться сообщение «Проверка соединения завершилась успешно». Нажмите кнопку **OК** , чтобы закрыть окно сообщения.  
  
6.  Нажмите кнопку **OК** , чтобы сохранить настройки диспетчера соединений.  
  
7.  Для использования диспетчера соединений, созданного на предыдущих шагах, в потоке данных пакета выберите источник или назначение OLE DB и настройте его.  
  
## <a name="see-also"></a>См. также  
 [Диспетчер соединений OLE DB](../../integration-services/connection-manager/ole-db-connection-manager.md)  
  
  
