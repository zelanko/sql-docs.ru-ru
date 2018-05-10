---
title: Источник BLOB-объекта Azure | Документы Майкрософт
ms.custom: ''
ms.date: 07/25/2016
ms.prod: sql
ms.prod_service: integration-services
ms.component: data-flow
ms.reviewer: ''
ms.suite: sql
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql13.dts.designer.afpblobsrc.f1
- sql14.dts.designer.afpblobsrc.f1
ms.assetid: 80645c5c-88c8-4fb0-8607-de1bb7bffcbb
caps.latest.revision: 12
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: d8066bcb801980cdae98620c25361ae358bb4fe3
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="azure-blob-source"></a>Компонент Azure Blob Source
  Компонент **Azure Blob Source** позволяет пакету служб SSIS считывать данные из большого двоичного объекта Azure. Поддерживаются следующие форматы файлов: CSV и AVRO.
  
  Чтобы отобразить редактор источников больших двоичных объектов Azure, перетащите компонент **Azure Blob Source** в конструктор потока данных и дважды щелкните его, чтобы открыть редактор.  
  
 Компонент **Источник BLOB-объекта Azure** входит в состав [пакета дополнительных компонентов SQL Server Integration Services (SSIS) для Azure](../../integration-services/azure-feature-pack-for-integration-services-ssis.md).  
  
1.  В поле **Диспетчер подключений службы хранилища Azure** укажите существующий диспетчер подключений службы хранилища Azure или создайте новый, который ссылается на учетную запись хранения Azure.  
  
2.  В поле **Имя контейнера больших двоичных объектов** укажите имя контейнера больших двоичных объектов, который содержит исходные файлы.  
  
3.  В поле **Имя большого двоичного объекта** укажите путь к большому двоичному объекту.  
  
4.  В поле **Формат файла большого двоичного объекта** укажите формат большого двоичного объекта, который следует использовать.  
  
5.  Если формат файла — CSV, необходимо указать значение **знака-разделителя столбцов** . Также выберите **Имена столбцов в первой строке данных** , если первая строка файла содержит имена столбцов.  
  
6.  После указания сведений о соединении переключитесь на страницу **Столбцы** , чтобы сопоставить столбцы источника со столбцами назначения для потока данных служб SSIS.  
  
  
