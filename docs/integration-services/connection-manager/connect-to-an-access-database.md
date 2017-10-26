---
title: "Соединение с базой данных Access | Документы Microsoft"
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
- Access [Integration Services]
- Access databases [Integration Services]
ms.assetid: 229fbd46-ef6a-4609-a4cc-d80d52c33cf1
caps.latest.revision: 18
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 2800075091835b2d6f2b07ee34e9b897fe86634e
ms.openlocfilehash: b5e60880b40a66a6f669bcfd53dcc59e497bbf0a
ms.contentlocale: ru-ru
ms.lasthandoff: 08/17/2017

---
# <a name="connect-to-an-access-database"></a>Подключение к базе данных Access
  Чтобы привязать пакет служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] к источнику данных Microsoft Office Access, нужны диспетчер соединений OLE DB и поставщик данных. Выбор поставщика данных зависит от версии Access, в которой был создан источник данных.  
  
-   Для файлов в формате Access 2003 и более ранних версий пакету требуется поставщик [!INCLUDE[msCoName](../../includes/msconame-md.md)] Jet OLE DB.  
  
-   Для формата Access 2007 пакету требуется поставщик данных OLE DB для компонента Microsoft Office 12.0 Access Database Engine.  
  
 Создать диспетчер соединений OLE DB и выбрать соответствующий поставщик данных можно либо из области «Диспетчеры соединений» в конструкторе служб [!INCLUDE[ssIS](../../includes/ssis-md.md)] , либо с помощью мастера импорта и экспорта [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
> [!NOTE]  
>  На 64-разрядном компьютере пакеты, которые соединяются с источниками данных [!INCLUDE[msCoName](../../includes/msconame-md.md)] Access, должны запускаться в 32-разрядном режиме. Поставщик [!INCLUDE[msCoName](../../includes/msconame-md.md)] OLE DB для Jet и поставщик OLE DB для ядра СУБД Microsoft Office 12.0 Access доступны только в 32-разрядных версиях.  

## <a name="connectivity-components-for-microsoft-excel-and-access-files"></a>Компоненты связи для файлов Microsoft Excel и Access
  
Может потребоваться загрузить компоненты связи для файлов Microsoft Office, если они еще не установлены. Загрузите последнюю версию компонентов подключения для Access и Excel файлов здесь: [доступа к базе данных ядро 2016 распространяемый компонент Microsoft](https://www.microsoft.com/download/details.aspx?id=54920).
  
Последнюю версию компонентов позволяет открывать файлы, созданные в предыдущих версиях доступ.

Если компьютер имеет 32-разрядной версии Office, необходимо установить 32-разрядную версию компонентов, а также необходимо гарантировать выполнение пакета в 32-разрядном режиме.

Если у вас есть подписка Office 365, убедитесь, что вы загрузите 2016 распространяемый доступа базы данных ядра и не 2016 среды выполнения Microsoft Access. При запуске программы установки может появиться сообщение об ошибке, что невозможно установить загрузки side-by-side работай компоненты Microsoft Office. Чтобы обойти это сообщение об ошибке, запустите установку в автоматическом режиме, открыв окно командной строки и выполнение. EXE-файла, загруженного с `/quiet` переключения. Например:

`C:\Users\<user name>\Downloads\AccessDatabaseEngine.exe /quiet`
  
## <a name="connecting-to-a-data-source-in-access-2003-or-earlier-format"></a>Соединение с источником данных в формате Access 2003 или более ранней версии  
  
### <a name="to-create-an-access-connection-manager-from-the-connection-managers-area"></a>Создание диспетчера соединений Access из области «Диспетчеры соединений»  
  
1.  Откройте пакет в среде [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)].  
  
2.  Щелкните правой кнопкой мыши в области **Диспетчеры соединений** , а затем выберите команду **Создать соединение OLE DB**.  
  
3.  В диалоговом окне **Настройка диспетчера соединений OLE DB** нажмите кнопку **Создать**.  
  
     Дополнительные сведения см. в статье [OLE DB Connection Manager](../../integration-services/connection-manager/ole-db-connection-manager.md).  
  
4.  В диалоговом окне **Диспетчер соединений** в поле **Поставщик**выберите поставщик **Microsoft Jet 4.0 OLE DB**, а затем настройте диспетчер соединений.  
  
### <a name="to-create-an-access-connection-from-the-sql-server-import-and-export-wizard"></a>Создание соединения Access с помощью мастера импорта и экспорта SQL Server  
  
1.  В среде [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]запустите мастер импорта и экспорта [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
2.  На странице **Выбор источника данных** выберите в поле **Источник данных**значение **Microsoft Access**, а затем настройте соединение Access.  
  
     При выборе в поле **Источник данных** значения **Microsoft Access**мастер автоматически создаст диспетчер соединений OLE DB с нужным поставщиком данных. Дополнительные сведения см. в статье [OLE DB Connection Manager](../../integration-services/connection-manager/ole-db-connection-manager.md).  
  
## <a name="connecting-to-a-data-source-in-access-2007-format"></a>Соединение с источником данных в формате Access 2007  
 Для доступа к источнику данных в формате Access 2007 диспетчеру соединений OLE DB требуется поставщик данных OLE DB для компонента Microsoft Office 12.0 Access Database Engine. Этот поставщик устанавливается автоматически вместе с системой [!INCLUDE[msCoName](../../includes/msconame-md.md)] Office 2007. Если система Office 2007 не установлена на компьютере, где работают службы [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] , необходимо отдельно установить поставщик. Чтобы установить поставщик OLE DB для ядра СУБД Microsoft Office 12.0 Access, скачайте и установите компоненты, расположенные на веб-странице [2007 Office System Driver: Data Connectivity Components](http://go.microsoft.com/fwlink/?LinkId=98155)(Системный драйвер Office 2007: компоненты связи с данными)  
  
### <a name="to-create-an-ole-db-connection-manager-from-the-connection-managers-area"></a>Создание диспетчера соединений OLE DB из области «Диспетчеры соединений»  
  
1.  Откройте пакет в среде [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)].  
  
2.  Щелкните правой кнопкой мыши в области **Диспетчеры соединений** , а затем выберите команду **Создать соединение OLE DB**.  
  
3.  В диалоговом окне **Настройка диспетчера соединений OLE DB** нажмите кнопку **Создать**.  
  
     Дополнительные сведения см. в статье [OLE DB Connection Manager](../../integration-services/connection-manager/ole-db-connection-manager.md).  
  
4.  В диалоговом окне **Диспетчер соединений** в поле **Поставщик**выберите поставщик **OLE DB для СУБД Microsoft Office 12.0 Access**, а затем настройте диспетчер соединений.  
  
    > [!NOTE]  
    >  Для соединения с источником данных, который использует Access 2007, выбирать в поле **Источник данных** значение **Поставщик Microsoft OLE DB для Jet 4.0**нельзя.  
  
### <a name="to-create-an-ole-db-connection-from-the-sql-server-import-and-export-wizard"></a>Создание соединения OLE DB из мастера импорта и экспорта SQL Server  
  
1.  В среде [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]запустите мастер импорта и экспорта [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
2.  В диалоговом окне **Выбор источника данных** в поле **Источник данных**выберите поставщик **OLE DB для СУБД Microsoft Office 12.0 Access**, а затем настройте соединение.  
  
    > [!NOTE]  
    >  Для соединения с источником данных, который использует Access 2007, выбирать в поле **Источник данных** значение **Поставщик Microsoft OLE DB для Jet 4.0**нельзя.  
  
     При выборе в поле **Источник данных** значения **поставщик OLE DB для СУБД Microsoft Office 12.0 Access**мастер автоматически создаст диспетчер соединения OLE DB с нужным поставщиком данных. Дополнительные сведения см. в статье [OLE DB Connection Manager](../../integration-services/connection-manager/ole-db-connection-manager.md).  
  
## <a name="see-also"></a>См. также раздел  
 [Подключение к книге Excel](../../integration-services/connection-manager/connect-to-an-excel-workbook.md)  
  
  

