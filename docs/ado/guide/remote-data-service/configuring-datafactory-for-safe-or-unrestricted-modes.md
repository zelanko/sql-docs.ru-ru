---
title: Настройка фабрики данных для безопасного или неограниченного режимов | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 11/09/2018
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- DataFactory configuration in RDS [ADO]
ms.assetid: 8ff24805-dc7a-42ae-b600-5bad0e3f51b8
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 32b87f7ddcd871748adbba66eb0a64a10204f0c1
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63214857"
---
# <a name="configuring-datafactory-for-safe-or-unrestricted-modes"></a>Настройка безопасного или неограниченного режимов в DataFactory
> [!IMPORTANT]
>  Начиная с Windows 8 и Windows Server 2012, серверные компоненты служб удаленных рабочих СТОЛОВ, больше не включаются в операционной системе Windows (см. в разделе Windows 8 и [настольная книга по совместимости Windows Server 2012](https://www.microsoft.com/download/details.aspx?id=27416) для получения дополнительных сведений). Клиентские компоненты служб удаленных рабочих СТОЛОВ будет поддерживаться в будущих версиях Windows. Избегайте использования этого компонента в новых разработках и запланируйте изменение существующих приложений, в которых он применяется. Приложения, использующие служб удаленных рабочих СТОЛОВ, следует перевести [WCF-сервиса данных](https://go.microsoft.com/fwlink/?LinkId=199565).  
  
 По умолчанию ADO устанавливается вместе с «safe» [RDSServer.DataFactory](../../../ado/reference/rds-api/datafactory-object-rdsserver.md) конфигурации. Безопасный режим для компонентов сервера служб удаленных рабочих СТОЛОВ означает, что выполняются следующие условия:  
  
1.  Обработчик должен иметь RDSServer.DataFactory, (это является обязательным компонентом параметр раздела реестра).  
  
2.  Обработчик по умолчанию, msdfmap.handler, зарегистрировано, присутствует в списке safe обработчик и помечена как обработчик по умолчанию.  
  
3.  Файл Msdfmap.ini устанавливается в каталоге Windows. Этот файл необходимо настроить в соответствии с потребностями, перед использованием служб удаленных рабочих СТОЛОВ в трехуровневом режиме.  
  
 При необходимости можно настроить неограниченное **DataFactory** установки. **DataFactory** можно использовать непосредственно без настраиваемого обработчика. Пользователи по-прежнему можно использовать пользовательский обработчик, изменив строки подключения, но это не обязательно. Дополнительные сведения о последствиях с помощью **RDSServer.DataFactory** объекта, см. в разделе [защита приложений RDS](../../../ado/guide/remote-data-service/securing-rds-applications.md).  
  
 Чтобы настроить записи реестра обработчика для безопасная конфигурация предоставляется handsafe.reg файл реестра. Для запуска в безопасном режиме, запустите handsafe.reg.  
  
 После выполнения handsafe.reg, необходимо остановить и перезапустить службу World Wide Web публикации веб-сервера, введя следующие команды в окне командной строки: «NET STOP W3SVC» и «W3SVC запустить NET».  
  
## <a name="see-also"></a>См. также  
 [Настройка DataFactory](../../../ado/guide/remote-data-service/datafactory-customization.md)   
 [Основные принципы RDS](../../../ado/guide/remote-data-service/rds-fundamentals.md)



