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
ms.translationtype: MT
ms.sourcegitcommit: 8397673c7ed9dfe8ae02871f9077ed7286e49863
ms.openlocfilehash: b23a158bff546fd6ffb4208638c039d690379ce1
ms.contentlocale: ru-ru
ms.lasthandoff: 08/09/2017

---
# <a name="odata-connection-manager"></a>Диспетчер соединений OData
  Диспетчер соединений OData позволяет подключаться к источнику OData. Компонент источника OData подключается к источнику OData с помощью диспетчера соединений OData и использует данные из службы. Дополнительные сведения см. в разделе [OData Source](../../integration-services/data-flow/odata-source.md).  
  
## <a name="adding-an-odata-connection-manager-to-an-ssis-package"></a>Добавление диспетчера соединений OData в пакет SSIS  
 Новый диспетчер соединений OData можно добавить в пакет служб SSIS тремя способами.  
  
-   Нажмите кнопку **Создать…** в **редакторе источника OData**  
  
-   Щелкните правой кнопкой мыши папку **Диспетчеры соединений** в **обозревателе решений**и выберите команду **Новый диспетчер соединений**. Для параметра **Тип диспетчера соединений** выберите **ODATA**.  
  
-   Щелкните правой кнопкой мыши панель **Диспетчеры соединений** в нижней части конструктора пакетов и выберите **Создать соединение…** Для параметра **Тип диспетчера соединений** выберите **ODATA**.  
  
## <a name="connection-manager-authentication"></a>Проверка подлинности диспетчера соединений  
 Диспетчер соединений OData поддерживает пять режимов проверки подлинности.  
  
-   Проверка подлинности Windows.  
  
-   Обычная проверка подлинности (с использованием имени пользователя и пароля)  

-   Microsoft Dynamics AX Online (с помощью имени пользователя и пароля)
  
-   Microsoft Dynamics CRM Online (с помощью имени пользователя и пароля)
  
-   Microsoft Online Services (с помощью имени пользователя и пароля)  
  
 Для анонимного доступа выберите режим проверки подлинности Windows.  
  
### <a name="specifying-and-securing-credentials"></a>Указание и защита учетных данных  
 Если служба OData использует обычную проверку подлинности, то можно указать имя пользователя и пароль в окне [Редактор диспетчера соединений OData](../../integration-services/connection-manager/odata-connection-manager-editor.md). Значения, указываемые в редакторе, сохраняются в пакете. Значение пароля шифруется в соответствии с уровнем защиты пакета.  
  
 Существует несколько способов параметризации значений имени пользователя и пароля или их хранения за пределами пакета. Например, это можно сделать с помощью параметров, а также непосредственно настроив свойства диспетчера соединений при запуске пакета с помощью среды SQL Server Management Studio.  
  
## <a name="odata-connection-manager-properties"></a>Свойства диспетчера соединений OData  
 В следующем списке описаны свойства диспетчера соединений OData.  
  
|||  
|-|-|  
|Свойство|Description|  
|Url|URL-адрес сервисного документа.|  
|UserName|Имя пользователя для обычной проверки подлинности.|  
|Пароль|Пароль, используемый для обычной проверки подлинности.|  
|ConnectionString|Отражает другие свойства диспетчера соединений.|  
  
## <a name="odata-connection-manager-editor"></a>Редактор диспетчера соединений c OData
  Диалоговое окно **Редактор диспетчера соединений c OData** служит для добавления нового или изменения существующего соединения с источником OData.  
  
### <a name="options"></a>Параметры  
 **Имя диспетчера подключений**  
 Имя диспетчера соединений.  
  
 **Расположение сервисного документа**  
 URL-адрес службы OData. Например, http://services.odata.org/V3/Northwind/Northwind.svc/.  
  
 **Проверка подлинности**  
 Выберите вариант **Проверка подлинности Windows** или **это имя пользователя и пароль** в поле **Обычная проверка подлинности**. Если выбран другой параметр, введите **имя пользователя** и **пароль**. 
 
 Теперь доступно три дополнительных варианта. Выберите **Microsoft Dynamics AX Online** для Dynamics AX Online, выберите **Microsoft Dynamics CRM Online** для Dynamics CRM Online и **Microsoft Online Services** для служб Microsoft Online Services. Если выбран один из этих трех вариантов, введите **имя пользователя** и **пароль**.
  
 **Проверка соединения**  
 Нажмите эту кнопку для проверки подключения к источнику OData.  
  
## <a name="see-also"></a>См. также:  
 [Редактор диспетчера подключений OData](../../integration-services/connection-manager/odata-connection-manager-editor.md)  
  
  
