---
title: Минимизация использования места в файле журнала | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 11/09/2018
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- log file space in RDS [ADO]
ms.assetid: 669662a0-e20f-483e-ab28-53f66c524c98
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 061cae6b387611886943aabcfa3dfd99579a59d7
ms.sourcegitcommit: 1a5448747ccb2e13e8f3d9f04012ba5ae04bb0a3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/12/2018
ms.locfileid: "51559817"
---
# <a name="minimizing-log-file-space-usage"></a>Минимизация использования места в файле журнала
Файл журнала может быстро заполнить (тем самым к остановке сервера), если имеется большое количество действий в базе данных SQL Server. Можно задать файл журнала **Truncate на контрольной точке** значительно расширить жизни файла журнала для базы данных.  
  
> [!IMPORTANT]
>  Начиная с Windows 8 и Windows Server 2012, серверные компоненты служб удаленных рабочих СТОЛОВ, больше не включаются в операционной системе Windows (см. в разделе Windows 8 и [настольная книга по совместимости Windows Server 2012](https://www.microsoft.com/download/details.aspx?id=27416) для получения дополнительных сведений). Клиентские компоненты служб удаленных рабочих СТОЛОВ будет поддерживаться в будущих версиях Windows. Избегайте использования этого компонента в новых разработках и запланируйте изменение существующих приложений, в которых он применяется. Приложения, использующие служб удаленных рабочих СТОЛОВ, следует перевести [WCF-сервиса данных](https://go.microsoft.com/fwlink/?LinkId=199565).  
  
### <a name="to-enable-truncate-on-checkpoint-in-microsoft-sql-server-65"></a>Чтобы включить Truncate на контрольной точке в Microsoft SQL Server 6.5  
  
1.  Запустите Microsoft SQL Server Enterprise Manager, откройте дерево для сервера и откройте дерево устройств базы данных.  
  
2.  Дважды щелкните имя базы данных, на котором эта функция включена.  
  
3.  Из **базы данных** выберите **Truncate**.  
  
4.  Из **параметры** выберите **усечение журнала на контрольной точке**, а затем нажмите кнопку **ОК**.  
  
### <a name="to-enable-truncate-on-checkpoint-in-microsoft-sql-server-70"></a>Чтобы включить Truncate на контрольной точке в Microsoft SQL Server 7.0  
  
1.  Запустите Microsoft SQL Server Enterprise Manager, откройте дерево для сервера и откройте дерево баз данных.  
  
2.  Щелкните правой кнопкой мыши имя базы данных, на котором эта функция будет включена и выберите **свойства**.  
  
3.  Из **параметры** выберите **усечение журнала на контрольной точке**, а затем нажмите кнопку **ОК**.  
  
 Дополнительные сведения о **Truncate на контрольной точке** компонентов, см. в документации Microsoft SQL Server.  
  
## <a name="see-also"></a>См. также  
 [Основные принципы RDS](../../../ado/guide/remote-data-service/rds-fundamentals.md)


