---
title: Подключение к книге Excel | Документы Майкрософт
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.suite: sql
ms.custom: ''
ms.technology: integration-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- Excel [Integration Services]
ms.assetid: d9746318-3669-4ce2-bbb0-4a1bd471c9dd
caps.latest.revision: 22
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: a8c9053eadc874599af454d784ca3994087d3d60
ms.sourcegitcommit: cc46afa12e890edbc1733febeec87438d6051bf9
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/12/2018
ms.locfileid: "35408406"
---
# <a name="connect-to-an-excel-workbook"></a>Подключение к книге Excel
  Чтобы соединить пакет служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] с книгой Microsoft Office Excel, нужен диспетчер соединений Excel.  
  
 Создать такие диспетчеры соединений можно либо в области «Диспетчеры соединений» конструктора служб [!INCLUDE[ssIS](../../includes/ssis-md.md)] , либо с помощью мастера импорта и экспорта [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
 
## <a name="connectivity-components-for-microsoft-excel-and-access-files"></a>Компоненты подключения для файлов Microsoft Excel и Access
  
Если компоненты подключения для файлов Microsoft Office еще не установлены, может потребоваться скачать их. Скачать последнюю версию компонентов подключения для файлов Excel и Access можно на следующей странице: [Распространяемый компонент ядра СУБД Microsoft Access 2016](https://www.microsoft.com/download/details.aspx?id=54920).
  
Последняя версия компонентов позволяет открывать файлы, созданные в более ранних версиях Excel.

Если на компьютере установлена 32-разрядная версия Office, нужно установить 32-разрядную версию компонентов, а также убедиться в том, что пакет запускается в 32-разрядном режиме.

Если у вас есть подписка на Office 365, нужно скачать распространяемый компонент ядра СУБД Access 2016, а не среду выполнения Microsoft Access 2016. При запуске установщика может появиться сообщение о том, что невозможно установить скачанные компоненты вместе с компонентами Office, полученными с помощью технологии "нажми и работай". Чтобы обойти это сообщение и успешно установить компоненты, запустите установку в тихом режиме. Для этого откройте окно командной строки и запустите скачанный EXE-файл с параметром `/quiet`. Пример:

`C:\Users\<user name>\Downloads\AccessDatabaseEngine.exe /quiet`

## <a name="create-an-excel-connection-manager"></a>Создание диспетчера подключений к Excel

### <a name="to-create-an-excel-connection-manager-from-the-connection-managers-area"></a>Создание диспетчера соединений Excel из области «Диспетчеры соединений»  
  
1.  Откройте пакет в среде [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)].  
  
2.  Щелкните правой кнопкой мыши в любом месте области **Диспетчеры соединений** и выберите **Создать соединение**.  
  
3.  В диалоговом окне **Добавление диспетчера соединений со службами SSIS** выберите **Excel**, а затем настройте диспетчер соединений.  
  
     Сведения о параметрах конфигурации для этого диспетчера соединений см. в разделе [Excel Connection Manager Editor](../../integration-services/connection-manager/excel-connection-manager-editor.md).  
  
### <a name="to-create-an-excel-connection-from-the-sql-server-import-and-export-wizard"></a>Создание соединения Excel с помощью мастера импорта и экспорта SQL Server  
  
1.  Запустите 32-разрядную версию мастера экспорта и импорта [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
2.  На странице **Выбор источника данных** выберите в поле **Источник данных**значение **Microsoft Excel**, а затем настройте соединение Excel.  
  
     Сведения о параметрах конфигурации для этого типа соединения см. в разделе [Excel Connection Manager Editor](../../integration-services/connection-manager/excel-connection-manager-editor.md).  
  
## <a name="see-also"></a>См. также:  
 [Подключение к базе данных Access](../../integration-services/connection-manager/connect-to-an-access-database.md)  
  
  
