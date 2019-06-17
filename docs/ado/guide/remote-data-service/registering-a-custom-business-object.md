---
title: Регистрация пользовательского бизнес-объекта | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 11/09/2018
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- custom business object in RDS [ADO]
- registering custom business objects in RDS [ADO]
- business objects in RDS [ADO]
ms.assetid: e9032ad8-d14c-42e3-ba13-cb5f00084a79
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 9db18a572fc82b05e75fb7bb286afb572fe500fd
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "66704234"
---
# <a name="registering-a-custom-business-object"></a>Регистрация пользовательского бизнес-объекта
Чтобы успешно запустить пользовательский бизнес-объект (.dll или .exe) через веб-сервер, ProgID бизнес-объект должен быть введен в реестре как описано в этой процедуре. Эта функция служб удаленных рабочих СТОЛОВ обеспечивает защиту безопасности веб-сервера, выполнив только санкционированные исполняемых файлов.  
  
> [!IMPORTANT]
>  Начиная с Windows 8 и Windows Server 2012, серверные компоненты служб удаленных рабочих СТОЛОВ, больше не включаются в операционной системе Windows (см. в разделе Windows 8 и [настольная книга по совместимости Windows Server 2012](https://www.microsoft.com/download/details.aspx?id=27416) для получения дополнительных сведений). Клиентские компоненты служб удаленных рабочих СТОЛОВ будет поддерживаться в будущих версиях Windows. Избегайте использования этого компонента в новых разработках и запланируйте изменение существующих приложений, в которых он применяется. Приложения, использующие служб удаленных рабочих СТОЛОВ, следует перевести [WCF-сервиса данных](https://go.microsoft.com/fwlink/?LinkId=199565).  
  
> [!NOTE]
>  Компоненты MDAC 2.0 и более поздние версии и Windows DAC, бизнес-объекта по умолчанию, [RDSServer.DataFactory](../../../ado/reference/rds-api/datafactory-object-rdsserver.md), не зарегистрирован по умолчанию во время установки MDAC/Windows DAC. Тем не менее если **RDSServer.DataFactory** был зарегистрирован как безопасные для выполнения на компьютере перед установкой, параметр поддерживается для новой установки.  
  
### <a name="to-register-a-custom-business-object"></a>Регистрация пользовательского бизнес-объекта:  
  
1.  Нажмите кнопку **запустить** и нажмите кнопку **запуска**.  
  
2.  Тип **RegEdit** и нажмите кнопку **ОК**.  
  
3.  В редакторе реестра перейдите к **HKEY_LOCAL_MACHINE\System\CurrentControlSet\Services\W3SVC\Parameters\ADCLaunch** раздел реестра.  
  
4.  Выберите **ADCLaunch** ключ, а затем из **изменить**последовательно выберите пункты **New** и нажмите кнопку **ключ**.  
  
5.  Введите идентификатор ProgID для пользовательских бизнес-объекта и нажмите кнопку **ввод**. Оставьте **значение** запись пустым.


