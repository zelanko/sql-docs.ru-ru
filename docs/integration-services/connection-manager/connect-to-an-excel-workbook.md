---
title: "Подключение к книге Excel | Документы Microsoft"
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Excel [Integration Services]
ms.assetid: d9746318-3669-4ce2-bbb0-4a1bd471c9dd
caps.latest.revision: 22
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 2800075091835b2d6f2b07ee34e9b897fe86634e
ms.openlocfilehash: f8fb1db80ac1b750950a3401516b54af5ee29686
ms.contentlocale: ru-ru
ms.lasthandoff: 08/17/2017

---
# <a name="connect-to-an-excel-workbook"></a>Подключение к книге Excel
  Чтобы соединить пакет служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] с книгой Microsoft Office Excel, нужен диспетчер соединений Excel.  
  
 Создать такие диспетчеры соединений можно либо в области «Диспетчеры соединений» конструктора служб [!INCLUDE[ssIS](../../includes/ssis-md.md)] , либо с помощью мастера импорта и экспорта [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
 
## <a name="connectivity-components-for-microsoft-excel-and-access-files"></a>Компоненты связи для файлов Microsoft Excel и Access
  
Может потребоваться загрузить компоненты связи для файлов Microsoft Office, если они еще не установлены. Загрузите последнюю версию компонентов подключения здесь файлов Excel и Access: [доступа к базе данных ядро 2016 распространяемый компонент Microsoft](https://www.microsoft.com/download/details.aspx?id=54920).
  
Последнюю версию компонентов позволяет открывать файлы, созданные в предыдущих версиях Excel.

Если компьютер имеет 32-разрядной версии Office, необходимо установить 32-разрядную версию компонентов, а также необходимо гарантировать выполнение пакета в 32-разрядном режиме.

Если у вас есть подписка Office 365, убедитесь, что вы загрузите 2016 распространяемый доступа базы данных ядра и не 2016 среды выполнения Microsoft Access. При запуске программы установки может появиться сообщение об ошибке, что невозможно установить загрузки side-by-side работай компоненты Microsoft Office. Чтобы обойти это сообщение об ошибке и установите компоненты успешно, запустите установку в автоматическом режиме, открыв окно командной строки и выполнение. EXE-файла, загруженного с `/quiet` переключения. Например:

`C:\Users\<user name>\Downloads\AccessDatabaseEngine.exe /quiet`

## <a name="create-an-excel-connection-manager"></a>Создайте диспетчер соединений с Excel

### <a name="to-create-an-excel-connection-manager-from-the-connection-managers-area"></a>Создание диспетчера соединений Excel из области «Диспетчеры соединений»  
  
1.  Откройте пакет в среде [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)].  
  
2.  Щелкните правой кнопкой мыши в любом месте области **Диспетчеры соединений** и выберите **Создать соединение**.  
  
3.  В диалоговом окне **Добавление диспетчера соединений со службами SSIS** выберите **Excel**, а затем настройте диспетчер соединений.  
  
     Сведения о параметрах конфигурации для этого диспетчера соединений см. в разделе [Excel Connection Manager Editor](../../integration-services/connection-manager/excel-connection-manager-editor.md).  
  
### <a name="to-create-an-excel-connection-from-the-sql-server-import-and-export-wizard"></a>Создание соединения Excel с помощью мастера импорта и экспорта SQL Server  
  
1.  Запустите 32-разрядную версию мастера экспорта и импорта [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
2.  На странице **Выбор источника данных** выберите в поле **Источник данных**значение **Microsoft Excel**, а затем настройте соединение Excel.  
  
     Сведения о параметрах конфигурации для этого типа соединения см. в разделе [Excel Connection Manager Editor](../../integration-services/connection-manager/excel-connection-manager-editor.md).  
  
## <a name="see-also"></a>См. также  
 [Подключение к базе данных Access](../../integration-services/connection-manager/connect-to-an-access-database.md)  
  
  

