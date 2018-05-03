---
title: Поставщики и компоненты службы | Документы Microsoft
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
- OLE DB providers [ADO]
- ADO, OLE DB providers
- service providers [ADO]
ms.assetid: 1fd7a374-587b-4ca9-9204-3a4019b67a71
caps.latest.revision: 14
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: e83cbfa4be055e5949b7ae15c9280a396b914950
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="service-providers-and-components"></a>Поставщики служб и компонентов
Поставщики услуг — компоненты, расширяющие функциональные возможности поставщиков данных, реализовав расширенные интерфейсы, которые изначально не поддерживаются в хранилище данных.  
  
 Предоставляет универсальный доступ к данным *архитектура компонентов* , позволяющий компонентов отдельных, специализированного для реализации отдельных наборов функциональных возможностей базы данных или «службы», поверх меньшими возможностями хранилищ. Таким образом вместо того чтобы принудительное предоставить собственную реализацию расширенных функций каждого из хранилищ данных или принудительное универсальных приложений для внутренней реализации функциональных возможностей базы данных, компоненты службы обеспечивают общую реализацию, которая может любое приложение Используйте при доступе к любому хранилищу данных. Тот факт, что некоторые функциональные возможности реализуется изначально хранилище данных, а также некоторые через общие компоненты прозрачно для приложения.  
  
 Например, механизм курсору, такие как [служба курсора для OLE DB](http://msdn.microsoft.com/en-us/57638feb-4ecd-4051-becb-8f828d21cf44), — это компонент службы, который может использовать данные из хранилища данных последовательные, и последовательного выводить прокручиваемый данные. Другие поставщики широко используются в ADO включают [поставщик Microsoft OLE DB сохраняемости (поставщик службы ADO)](../../../ado/guide/appendixes/microsoft-ole-db-persistence-provider-ado-service-provider.md) (для сохранения данных в файле), [службы Microsoft Data Shaping Service для OLE DB (ADO поставщиком услуг) ](../../../ado/guide/appendixes/microsoft-data-shaping-service-for-ole-db-ado-service-provider.md) (для иерархических **наборы записей**) и [поставщик Microsoft OLE DB удаленного взаимодействия (поставщик службы ADO)](../../../ado/guide/appendixes/microsoft-ole-db-remoting-provider-ado-service-provider.md) (для вызова поставщиков данных на удаленном компьютере).  
  
 Дополнительные сведения о службе и поставщики данных см. в разделе [приложение A: поставщики](../../../ado/guide/appendixes/appendix-a-providers.md).
