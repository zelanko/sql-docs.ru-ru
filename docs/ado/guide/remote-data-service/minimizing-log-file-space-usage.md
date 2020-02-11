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
ms.openlocfilehash: c8dc0799fbeba24ad4725d25647ef471edad8fb7
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "67922557"
---
# <a name="minimizing-log-file-space-usage"></a>Минимизация использования места в файле журнала
Файл журнала может быстро заполняться (таким же прерывает работу сервера), если в SQL Server базе данных имеется большой объем действий. Можно задать усечение файла журнала **на контрольную точку** , чтобы значительно продлить время существования файла журнала для базы данных.  
  
> [!IMPORTANT]
>  Начиная с Windows 8 и Windows Server 2012, компоненты RDS больше не включены в операционную систему Windows (Дополнительные сведения см. в статье о совместимости Windows 8 и [Windows server 2012 Cookbook](https://www.microsoft.com/download/details.aspx?id=27416) ). Клиентские компоненты RDS будут удалены в следующей версии Windows. Избегайте использования этого компонента в новых разработках и запланируйте изменение существующих приложений, в которых он применяется. Приложения, использующие RDS, должны переноситься в [службу данных WCF](https://go.microsoft.com/fwlink/?LinkId=199565).  
  
### <a name="to-enable-truncate-on-checkpoint-in-microsoft-sql-server-65"></a>Включение усечения для контрольной точки в Microsoft SQL Server 6,5  
  
1.  Запустите диспетчер Microsoft SQL Server Enterprise, откройте дерево для сервера, а затем откройте дерево устройства базы данных.  
  
2.  Дважды щелкните имя базы данных, в которой будет включена эта функция.  
  
3.  На вкладке **база данных** выберите **усечение**.  
  
4.  На вкладке **Параметры** выберите **усечение журнала на контрольной точке**, а затем нажмите кнопку **ОК**.  
  
### <a name="to-enable-truncate-on-checkpoint-in-microsoft-sql-server-70"></a>Включение усечения для контрольной точки в Microsoft SQL Server 7,0  
  
1.  Запустите диспетчер Microsoft SQL Server Enterprise, откройте дерево для сервера, а затем откройте дерево базы данных.  
  
2.  Щелкните правой кнопкой мыши имя базы данных, в которой будет включена эта функция, и выберите пункт **Свойства**.  
  
3.  На вкладке **Параметры** выберите **усечение журнала на контрольной точке**, а затем нажмите кнопку **ОК**.  
  
 Дополнительные сведения о функции **Truncate on Checkpoint** см. в документации по Microsoft SQL Server.  
  
## <a name="see-also"></a>См. также:  
 [Основные принципы RDS](../../../ado/guide/remote-data-service/rds-fundamentals.md)


