---
title: Запуск бизнес-объектов в службах компонентов | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 11/09/2018
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- component services in RDS [ADO]
ms.assetid: 3077d0b6-42d6-4f10-8e5d-42e6204f1109
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 4ddf5fff0974c9a7ae92b5d44372f0d71fecf712
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63191794"
---
# <a name="running-business-objects-in-component-services"></a>Запуск бизнес-объектов в службах компонентов
> [!IMPORTANT]
>  Начиная с Windows 8 и Windows Server 2012, серверные компоненты служб удаленных рабочих СТОЛОВ, больше не включаются в операционной системе Windows (см. в разделе Windows 8 и [настольная книга по совместимости Windows Server 2012](https://www.microsoft.com/download/details.aspx?id=27416) для получения дополнительных сведений). Клиентские компоненты служб удаленных рабочих СТОЛОВ будет поддерживаться в будущих версиях Windows. Избегайте использования этого компонента в новых разработках и запланируйте изменение существующих приложений, в которых он применяется. Приложения, использующие служб удаленных рабочих СТОЛОВ, следует перевести [WCF-сервиса данных](https://go.microsoft.com/fwlink/?LinkId=199565).  
  
 Бизнес-объектов может быть исполняемые файлы (.exe) или библиотеки динамической компоновки (.dll). Конфигурация, используемая для запуска бизнес-объекта зависит от того, является ли объект файл .dll или .exe:  
  
-   Бизнес-объекты, созданные как файлы .exe можно вызывать с помощью DCOM. Если эти бизнес-объекты используются через Internet Information Services (IIS), они подвержены дополнительных маршалинг данных, что приведет к снижению производительности клиента.  
  
-   Бизнес-объекты, созданные как DLL-файлы можно использовать с помощью IIS и поэтому также по протоколу HTTP. Они могут также использоваться через DCOM только с помощью служб компонентов, или с помощью Microsoft Transaction Server, если вы используете Windows NT. Бизнес-объект библиотеки DLL будет должны быть зарегистрированы на компьютере сервера IIS для доступа к ним с помощью IIS. Сведения о настройке запуска библиотеки DLL в DCOM см. в разделе разделе [Включение библиотеки DLL для работы на DCOM](../../../ado/guide/remote-data-service/enabling-a-dll-to-run-on-dcom.md).  
  
> [!NOTE]
>  Если при реализации бизнес-объектов на среднем уровне как компоненты службы компонентов с помощью **GetObjectContext**, **SetComplete**, и **SetAbort**, бизнеса объекты могут использовать службы компонентов (или MTS, если вы используете Windows NT) объекты контекста для сохраняют свое состояние между вызовами клиента. Этот сценарий возможен с помощью DCOM, которая обычно реализуется между доверенные клиенты и серверы в интрасети. В этом случае [RDS. Пространство данных](../../../ado/reference/rds-api/dataspace-object-rds.md) объекта и [CreateObject](../../../ado/reference/rds-api/createobject-method-rds.md) метод на стороне клиента заменяются объект контекста транзакции и **CreateInstance** метода, которые предоставляются элементом **ITransactionContext** интерфейса и реализуется службы компонентов.  
  
## <a name="see-also"></a>См. также  
 [Основные принципы RDS](../../../ado/guide/remote-data-service/rds-fundamentals.md)


