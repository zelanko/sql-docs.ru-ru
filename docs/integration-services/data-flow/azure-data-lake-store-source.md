---
title: "Источник Azure Data Lake Store | Документы Майкрософт"
ms.custom: 
ms.date: 03/02/2017
ms.prod: sql-non-specified
ms.prod_service: integration-services
ms.service: 
ms.component: data-flow
ms.reviewer: 
ms.suite: sql
ms.technology: integration-services
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- SQL13.DTS.DESIGNER.AFPADLSSRC.F1
- sql14.dts.designer.afpadlssrc.f1
ms.assetid: f9c3311f-7316-48d6-bf10-d810e70b4304
caps.latest.revision: "10"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 927ce3e1d364ab7fe4c4ba45e96c8dec5d62fbe4
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/20/2017
---
# <a name="azure-data-lake-store-source"></a>Источник Azure Data Lake Store
  Компонент **Источник Azure Data Lake Store** позволяет пакету служб SSIS считывать данные из Azure Data Lake Store. Поддерживаются следующие форматы файлов: текст и AVRO.
  
 Компонент **Источник Azure Data Lake Store** входит в состав [пакета дополнительных компонентов SQL Server Integration Services (SSIS) для Azure](../../integration-services/azure-feature-pack-for-integration-services-ssis.md).  
  
>   [!NOTE]
> Чтобы диспетчер подключений Azure Data Lake Store и компоненты, которые его используют (т. е. источник и цель Azure Data Lake Store), могли подключаться к службам, убедитесь, что вы скачали последнюю версию пакета дополнительных компонентов Azure [здесь](https://www.microsoft.com/download/details.aspx?id=49492). 
  
## <a name="configure-the-azure-data-lake-store-source"></a>Настройка источника Azure Data Lake Store
 1. Чтобы отобразить редактор для источника Azure Data Lake Store, перетащите компонент **Источник Azure Data Lake Store** в конструктор потока данных и дважды щелкните его, чтобы открыть редактор.  
  
2.  В поле **Диспетчер подключений Azure Data Lake Store** укажите существующий диспетчер подключений Azure Data Lake Store или создайте новый диспетчер, который ссылается на службу Azure Data Lake Store.  
  
    1.  В поле **Путь к файлу** укажите путь к исходному файлу в Azure Data Lake Store.   
  
    2.  В поле **Формат файла** укажите формат исходного файла.  
  
        Если формат файла — "Текст", необходимо указать значение **символа-разделителя столбцов** . Также выберите **Имена столбцов в первой строке данных** , если первая строка файла содержит имена столбцов.  
  
3.  После указания сведений о соединении переключитесь на страницу **Столбцы** , чтобы сопоставить столбцы источника со столбцами назначения для потока данных служб SSIS.   
