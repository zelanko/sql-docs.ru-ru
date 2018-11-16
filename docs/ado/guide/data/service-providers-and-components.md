---
title: Поставщики услуг и компоненты | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- OLE DB providers [ADO]
- ADO, OLE DB providers
- service providers [ADO]
ms.assetid: 1fd7a374-587b-4ca9-9204-3a4019b67a71
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 050d1c9ec8aa5a158d5c08fb77d3743e55567699
ms.sourcegitcommit: 63b4f62c13ccdc2c097570fe8ed07263b4dc4df0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/13/2018
ms.locfileid: "51602244"
---
# <a name="service-providers-and-components"></a>Поставщики служб и компоненты
Поставщики услуг — это компоненты, которые расширяют функциональные возможности поставщиков данных, реализовав расширенные интерфейсы, которые изначально не поддерживаются хранилищем данных.  
  
 Предоставляет универсальный доступ к данным *архитектура компонентов* , позволяющий компонентов отдельных, специализированного для реализации отдельных наборов функций базы данных или «службы», поверх меньшими возможностями хранилищ. Таким образом вместо того, чтобы принудительно каждого хранилища данных, чтобы предоставить собственную реализацию расширенных функциональных возможностей или принудительное универсальных приложений для внутренней реализации функциональности базы данных, компоненты службы обеспечивают общую реализацию, которая может любое приложение Используйте при доступе к любому хранилищу данных. Тот факт, что некоторые функции в собственном коде реализуется по хранилищу данных, а часть — через общие компоненты является прозрачным для приложения.  
  
 Например, механизм курсора, таких как [служба курсора для OLE DB](https://msdn.microsoft.com/57638feb-4ecd-4051-becb-8f828d21cf44), — это компонент службы, использующие данные из хранилища данных последовательных, последовательного прокручиваемые данные. Включать других поставщиков услуг, часто используемые ADO [поставщик Microsoft OLE DB сохраняемости (поставщик услуг ADO)](../../../ado/guide/appendixes/microsoft-ole-db-persistence-provider-ado-service-provider.md) (для сохранения данных в файл), [службы Microsoft Data Shaping Service для OLE DB (поставщик услуг ADO) ](../../../ado/guide/appendixes/microsoft-data-shaping-service-for-ole-db-ado-service-provider.md) (для иерархических **наборы записей**) и [поставщик Microsoft OLE DB удаленного взаимодействия (поставщик услуг ADO)](../../../ado/guide/appendixes/microsoft-ole-db-remoting-provider-ado-service-provider.md) (для вызова поставщиков данных на удаленном компьютере).  
  
 Дополнительные сведения о службе и поставщики данных, см. в разделе [приложение а. Поставщики](../../../ado/guide/appendixes/appendix-a-providers.md).
