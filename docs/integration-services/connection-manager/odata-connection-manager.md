---
title: "Диспетчер соединений OData | Документы Microsoft"
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3caa4372-aff3-4c0f-9ecd-97870948b8d0
caps.latest.revision: 9
f1_keywords:
- sql13.dts.designer.odatasource.connectionmanager.f1
- sql13.dts.designer.odataconnectionmanager.f1
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 21f0cfd102a6fcc44dfc9151750f1b3c936aa053
ms.openlocfilehash: f54562b59e8c61f723c17e2812ca39cb2e95f273
ms.contentlocale: ru-ru
ms.lasthandoff: 08/28/2017

---
# <a name="odata-connection-manager"></a>Диспетчер соединений OData
 Подключиться к источнику данных OData с помощью диспетчера соединений OData. Компонент источника OData использует диспетчер соединений OData для подключения к источнику данных OData и получать данные из службы. Дополнительные сведения см. в разделе [OData Source](../../integration-services/data-flow/odata-source.md).  
  
## <a name="adding-an-odata-connection-manager-to-an-ssis-package"></a>Добавление диспетчера соединений OData в пакет SSIS  
 Новый диспетчер соединений OData можно добавить к пакету служб SSIS тремя способами:  
  
-   Нажмите кнопку **Создать…** в **редакторе источника OData**  
  
-   Щелкните правой кнопкой мыши папку **Диспетчеры соединений** в **обозревателе решений**и выберите команду **Новый диспетчер соединений**. Для параметра **Тип диспетчера соединений** выберите **ODATA**.  
  
-   Щелкните правой кнопкой мыши **диспетчеры соединений** панели в нижней части конструктора, а затем выберите пакет **новое соединение**. Для параметра **Тип диспетчера соединений** выберите **ODATA**.  
  
## <a name="connection-manager-authentication"></a>Проверка подлинности диспетчера соединений  
 Диспетчер соединений OData поддерживает пять режимов проверки подлинности.  
  
-   Проверка подлинности Windows.  
  
-   Обычная проверка подлинности (с использованием имени пользователя и пароля)  

-   Microsoft Dynamics AX Online (с помощью имени пользователя и пароля)
  
-   Microsoft Dynamics CRM Online (с помощью имени пользователя и пароля)
  
-   Microsoft Online Services (с помощью имени пользователя и пароля)  
  
Для анонимного доступа выберите режим проверки подлинности Windows.  

Чтобы подключиться к Microsoft Dynamics AX Online или Microsoft Dynamics CRM online, нельзя использовать **Microsoft Online Services** вариант проверки подлинности. Также нельзя использовать любой параметр, который настроен для многофакторной проверки подлинности.
  
### <a name="specifying-and-securing-credentials"></a>Указание и защита учетных данных  
 Если служба OData использует обычную проверку подлинности, то можно указать имя пользователя и пароль в окне [Редактор диспетчера соединений OData](../../integration-services/connection-manager/odata-connection-manager-editor.md). Значения, указываемые в редакторе, сохраняются в пакете. Значение пароля шифруется в соответствии с уровнем защиты пакета.  
  
 Существует несколько способов параметризации значений имени пользователя и пароля или их хранения за пределами пакета. Например можно использовать параметры, или установить свойства диспетчера соединений непосредственно при запуске пакета из среды SQL Server Management Studio.  
  
## <a name="odata-connection-manager-properties"></a>Свойства диспетчера соединений OData  
 Ниже перечислены свойства диспетчера соединений OData.  
  
|||  
|-|-|  
|property|Description|  
|Url|URL-адрес сервисного документа.|  
|UserName|Имя пользователя для проверки подлинности, если это необходимо.|  
|Пароль|Пароль для проверки подлинности, если это необходимо.|  
|ConnectionString|Включает другие свойства диспетчера соединений.|  
  
## <a name="odata-connection-manager-editor"></a>Редактор диспетчера соединений c OData
  Используйте **редактор диспетчера соединений OData** диалогового окна для добавления соединения или изменить существующее подключение к источнику данных OData.  
  
### <a name="options"></a>Параметры  
 **Имя диспетчера подключений**  
 Имя диспетчера соединений.  
  
 **Расположение сервисного документа**  
 URL-адрес службы OData. Например, http://services.odata.org/V3/Northwind/Northwind.svc/.  
  
 **Проверка подлинности**  
Выберите один из следующих вариантов.
-   **Проверка подлинности Windows**. Выбирайте этот параметр для анонимного доступа.
-   **Обычная проверка подлинности** 
-   **Microsoft Dynamics AX сети** для Dynamics AX в интерактивном режиме
-   **Microsoft Dynamics CRM Online** для Dynamics CRM Online
-   **Microsoft Online Services** служб Microsoft Online Services

Если выбран параметр, отличный от проверки подлинности Windows, введите **имя пользователя** и **пароль**. 

Чтобы подключиться к Microsoft Dynamics AX Online или Microsoft Dynamics CRM online, нельзя использовать **Microsoft Online Services** вариант проверки подлинности. Также нельзя использовать любой параметр, который настроен для многофакторной проверки подлинности.

 **Проверка соединения**  
 Нажмите эту кнопку, чтобы проверить соединение с источником OData.  

