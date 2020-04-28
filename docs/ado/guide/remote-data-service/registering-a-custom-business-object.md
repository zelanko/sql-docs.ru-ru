---
title: Регистрация настраиваемого бизнес-объекта | Документация Майкрософт
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
ms.openlocfilehash: f998463e0f8190aa040b801d2fd29c732bb31dce
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "67922368"
---
# <a name="registering-a-custom-business-object"></a>Регистрация пользовательского бизнес-объекта
Для успешного запуска пользовательского бизнес-объекта (. dll или. exe) через веб-сервер в реестр необходимо указать ProgID бизнес-объекта, как описано в этой процедуре. Эта функция RDS обеспечивает защиту веб-сервера, запуская только санкционированные исполняемые файлы.  
  
> [!IMPORTANT]
>  Начиная с Windows 8 и Windows Server 2012, компоненты RDS больше не включены в операционную систему Windows (Дополнительные сведения см. в статье о совместимости Windows 8 и [Windows server 2012 Cookbook](https://www.microsoft.com/download/details.aspx?id=27416) ). Клиентские компоненты RDS будут удалены в следующей версии Windows. Избегайте использования этого компонента в новых разработках и запланируйте изменение существующих приложений, в которых он применяется. Приложения, использующие RDS, должны переноситься в [службу данных WCF](https://go.microsoft.com/fwlink/?LinkId=199565).  
  
> [!NOTE]
>  Для компонентов MDAC 2,0 и более поздних версий и приложений Windows DAC по умолчанию бизнес-объект [RDSServer.](../../../ado/reference/rds-api/datafactory-object-rdsserver.md)DataObject не регистрируется по умолчанию во время установки MDAC или приложения уровня данных Windows. Однако если **RDSServer. объект факта** был зарегистрирован в качестве безопасного для выполнения на компьютере до установки, запись реестра будет сохранена для новой установки.  
  
### <a name="to-register-a-custom-business-object"></a>Чтобы зарегистрировать настраиваемый бизнес-объект, выполните следующие действия.  
  
1.  Нажмите кнопку **Пуск** и выберите команду **выполнить**.  
  
2.  Введите **regedit** и нажмите кнопку **ОК**.  
  
3.  В редакторе реестра перейдите к разделу реестра **HKEY_LOCAL_MACHINE \system\currentcontrolset\services\w3svc\parameters\adclaunch** .  
  
4.  Выберите ключ **адклаунч** , а затем в меню **Правка**наведите указатель мыши на пункт **создать** и выберите **ключ**.  
  
5.  Введите идентификатор ProgID для настраиваемого бизнес-объекта и нажмите клавишу **Ввод**. Оставьте поле **значение** пустым.


