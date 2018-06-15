---
title: Минимизация использования пространства журнала файла | Документы Microsoft
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- log file space in RDS [ADO]
ms.assetid: 669662a0-e20f-483e-ab28-53f66c524c98
caps.latest.revision: 14
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 75091ba881fde2c464ae6e184bd747cc70b42790
ms.sourcegitcommit: 62826c291db93c9017ae219f75c3cfeb8140bf06
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/11/2018
ms.locfileid: "35274183"
---
# <a name="minimizing-log-file-space-usage"></a>Минимизация использования пространства для файла журнала
Файл журнала может быстро заполнить (таким образом, остановка работы сервера) при наличии большого объема действий на базе данных Microsoft SQL Server. Можно задать файл журнала **Truncate на контрольной точке** позволяет значительно увеличить ресурсы файла журнала для базы данных.  
  
> [!IMPORTANT]
>  Начиная с Windows 8 и Windows Server 2012, серверные компоненты служб удаленных рабочих СТОЛОВ больше не включаются в операционной системе Windows (в разделе Windows 8 и [руководство по Windows Server 2012 совместимости](https://www.microsoft.com/en-us/download/details.aspx?id=27416) для получения дополнительных сведений). Клиентские компоненты служб удаленных рабочих СТОЛОВ будут удалены в будущих версиях Windows. Избегайте использования этого компонента в новых разработках и запланируйте изменение существующих приложений, в которых он применяется. Приложения, использующие служб удаленных рабочих СТОЛОВ необходимо перенести в [службы данных WCF](http://go.microsoft.com/fwlink/?LinkId=199565).  
  
### <a name="to-enable-truncate-on-checkpoint-in-microsoft-sql-server-65"></a>Чтобы включить Truncate на контрольную точку в Microsoft SQL Server 6.5  
  
1.  Запустите Microsoft SQL Server Enterprise Manager, откройте дерево для сервера и откройте дерево базы данных устройства.  
  
2.  Дважды щелкните имя базы данных, на котором эта функция включена.  
  
3.  Из **базы данных** выберите **Truncate**.  
  
4.  Из **параметры** выберите **усечение журнала на контрольной точке**, а затем нажмите кнопку **ОК**.  
  
### <a name="to-enable-truncate-on-checkpoint-in-microsoft-sql-server-70"></a>Чтобы включить Truncate на контрольную точку в Microsoft SQL Server 7.0  
  
1.  Запустите Microsoft SQL Server Enterprise Manager, откройте дерево для сервера и откройте дерево баз данных.  
  
2.  Щелкните правой кнопкой мыши имя базы данных, на котором эта функция будет включена и выберите **свойства**.  
  
3.  Из **параметры** выберите **усечение журнала на контрольной точке**, а затем нажмите кнопку **ОК**.  
  
 Дополнительные сведения о **Truncate на контрольной точке** компонента, см. в документации Microsoft SQL Server.  
  
## <a name="see-also"></a>См. также  
 [Основные принципы RDS](../../../ado/guide/remote-data-service/rds-fundamentals.md)


