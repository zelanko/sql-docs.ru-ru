---
title: "Выполнение бизнес-объектов в службах компонентов | Документы Microsoft"
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: guide
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- component services in RDS [ADO]
ms.assetid: 3077d0b6-42d6-4f10-8e5d-42e6204f1109
caps.latest.revision: 17
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: a4c05f997a09e2a3368c47ce5038c17421867172
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="running-business-objects-in-component-services"></a>Выполнение бизнес-объектов в службах компонентов
> [!IMPORTANT]
>  Начиная с Windows 8 и Windows Server 2012, серверные компоненты служб удаленных рабочих СТОЛОВ больше не включаются в операционной системе Windows (в разделе Windows 8 и [руководство по Windows Server 2012 совместимости](https://www.microsoft.com/en-us/download/details.aspx?id=27416) для получения дополнительных сведений). Клиентские компоненты служб удаленных рабочих СТОЛОВ будут удалены в будущих версиях Windows. Избегайте использования этого компонента в новых разработках и запланируйте изменение существующих приложений, в которых он применяется. Приложения, использующие служб удаленных рабочих СТОЛОВ необходимо перенести в [службы данных WCF](http://go.microsoft.com/fwlink/?LinkId=199565).  
  
 Бизнес-объектов может быть исполняемые файлы (.exe) или библиотеки динамической компоновки (DLL). Конфигурация, используемая для запуска бизнес-объекта зависит от того, является ли объект файл .dll или .exe:  
  
-   Бизнес-объекты, созданные как файлы .exe можно вызвать через DCOM. Если эти бизнес-объектов используются через Internet Information Services (IIS), они подвержены маршалинг дополнительные данные, что приведет к снижению производительности клиента.  
  
-   Бизнес-объектов, создан в виде DLL-файлы можно использовать через службы IIS и, следовательно, по протоколу HTTP. Они могут также использоваться через DCOM только с помощью служб компонентов или с помощью Microsoft Transaction Server, если вы используете Windows NT. Бизнес-объекта, библиотеки DLL будет необходимо зарегистрировать на компьютере сервера IIS для доступа к ним через службы IIS. Сведения о настройке библиотеки DLL для запуска на DCOM см. в разделе [Включение DLL для работы на DCOM](../../../ado/guide/remote-data-service/enabling-a-dll-to-run-on-dcom.md).  
  
> [!NOTE]
>  Если бизнес-объектов на среднем уровне реализуются как компоненты служб компонентов с помощью **GetObjectContext**, **SetComplete**, и **SetAbort**, бизнеса объекты могут использовать службы компонентов (или MTS, если вы используете Windows NT) объекты контекста для поддержания свое состояние между несколькими вызовами клиента. Этот сценарий возможен с помощью DCOM, который обычно реализуется между доверенных клиентов и серверов в интрасети. В этом случае [RDS. Пространство данных](../../../ado/reference/rds-api/dataspace-object-rds.md) объекта и [CreateObject](../../../ado/reference/rds-api/createobject-method-rds.md) метод на стороне клиента заменяются объект контекста транзакции и **CreateInstance** метод, предоставляемых **ITransactionContext** интерфейса и реализуется служб компонентов.  
  
## <a name="see-also"></a>См. также:  
 [Основные принципы RDS](../../../ado/guide/remote-data-service/rds-fundamentals.md)



