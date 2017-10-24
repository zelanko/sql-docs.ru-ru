---
title: "Поставщики и компоненты службы | Документы Microsoft"
ms.prod: sql-non-specified
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- OLE DB providers [ADO]
- ADO, OLE DB providers
- service providers [ADO]
ms.assetid: 1fd7a374-587b-4ca9-9204-3a4019b67a71
caps.latest.revision: 14
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: c8f574b00b5c53caef2184d2923e79746d3ef56c
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="service-providers-and-components"></a>Поставщики служб и компонентов
Поставщики услуг — компоненты, расширяющие функциональные возможности поставщиков данных, реализовав расширенные интерфейсы, которые изначально не поддерживаются в хранилище данных.  
  
 Предоставляет универсальный доступ к данным *архитектура компонентов* , позволяющий компонентов отдельных, специализированного для реализации отдельных наборов функциональных возможностей базы данных или «службы», поверх меньшими возможностями хранилищ. Таким образом вместо того чтобы принудительное предоставить собственную реализацию расширенных функций каждого из хранилищ данных или принудительное универсальных приложений для внутренней реализации функциональных возможностей базы данных, компоненты службы обеспечивают общую реализацию, которая может любое приложение Используйте при доступе к любому хранилищу данных. Тот факт, что некоторые функциональные возможности реализуется изначально хранилище данных, а также некоторые через общие компоненты прозрачно для приложения.  
  
 Например, механизм курсору, такие как [служба курсора для OLE DB](http://msdn.microsoft.com/en-us/57638feb-4ecd-4051-becb-8f828d21cf44), — это компонент службы, который может использовать данные из хранилища данных последовательные, и последовательного выводить прокручиваемый данные. Другие поставщики широко используются в ADO включают [поставщик Microsoft OLE DB сохраняемости (поставщик службы ADO)](../../../ado/guide/appendixes/microsoft-ole-db-persistence-provider-ado-service-provider.md) (для сохранения данных в файле), [службы Microsoft Data Shaping Service для OLE DB (ADO поставщиком услуг) ](../../../ado/guide/appendixes/microsoft-data-shaping-service-for-ole-db-ado-service-provider.md) (для иерархических **наборы записей**) и [поставщик Microsoft OLE DB удаленного взаимодействия (поставщик службы ADO)](../../../ado/guide/appendixes/microsoft-ole-db-remoting-provider-ado-service-provider.md) (для вызова поставщиков данных на удаленном компьютере).  
  
 Дополнительные сведения о службе и поставщики данных см. в разделе [приложение A: поставщики](../../../ado/guide/appendixes/appendix-a-providers.md).

