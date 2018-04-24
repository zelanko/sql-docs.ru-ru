---
title: Регистрация пользовательских бизнес-объект | Документы Microsoft
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: ado
ms.technology:
- drivers
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- custom business object in RDS [ADO]
- registering custom business objects in RDS [ADO]
- business objects in RDS [ADO]
ms.assetid: e9032ad8-d14c-42e3-ba13-cb5f00084a79
caps.latest.revision: 19
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: fd6bd1d650f3aedabe1f6b13bc0503e0961b7ffe
ms.sourcegitcommit: bb044a48a6af9b9d8edb178dc8c8bd5658b9ff68
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/18/2018
---
# <a name="registering-a-custom-business-object"></a>Регистрация пользовательских бизнес-объект
Чтобы успешно запустить пользовательский бизнес-объект (.dll или .exe) через веб-сервер, ProgID бизнес-объект должен быть введен в реестре как описано в этой процедуре. Эта функция служб удаленных рабочих СТОЛОВ защищает безопасности веб-сервера, запустив только санкционированные исполняемые файлы.  
  
> [!IMPORTANT]
>  Начиная с Windows 8 и Windows Server 2012, серверные компоненты служб удаленных рабочих СТОЛОВ больше не включаются в операционной системе Windows (в разделе Windows 8 и [руководство по Windows Server 2012 совместимости](https://www.microsoft.com/en-us/download/details.aspx?id=27416) для получения дополнительных сведений). Клиентские компоненты служб удаленных рабочих СТОЛОВ будут удалены в будущих версиях Windows. Избегайте использования этого компонента в новых разработках и запланируйте изменение существующих приложений, в которых он применяется. Приложения, использующие служб удаленных рабочих СТОЛОВ необходимо перенести в [службы данных WCF](http://go.microsoft.com/fwlink/?LinkId=199565).  
  
> [!NOTE]
>  Компоненты MDAC 2.0 и более поздней версии и Windows DAC, бизнес-объекта по умолчанию, [RDSServer.DataFactory](../../../ado/reference/rds-api/datafactory-object-rdsserver.md), не регистрируется по умолчанию во время установки компонентов MDAC, Windows DAC. Однако если **RDSServer.DataFactory** зарегистрирован как безопасный для выполнения на компьютере перед установкой параметра реестра сохраняется для новой установки.  
  
### <a name="to-register-a-custom-business-object"></a>Чтобы зарегистрировать пользовательский бизнес-объект:  
  
1.  Нажмите кнопку **запустить** и нажмите кнопку **запуска**.  
  
2.  Тип **RegEdit** и нажмите кнопку **ОК**.  
  
3.  В редакторе реестра перейдите к **HKEY_LOCAL_MACHINE\System\CurrentControlSet\Services\W3SVC\Parameters\ADCLaunch** раздел реестра.  
  
4.  Выберите **ADCLaunch** ключа, а затем из **изменить**последовательно выберите пункты **New** и нажмите кнопку **ключ**.  
  
5.  Введите идентификатор ProgID пользовательский бизнес-объект и нажмите кнопку **ввод**. Оставить **значение** входа с пустым.


