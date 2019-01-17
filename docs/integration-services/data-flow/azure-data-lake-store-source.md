---
title: Источник Azure Data Lake Store | Документы Майкрософт
ms.custom: ''
ms.date: 08/16/2018
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- SQL13.DTS.DESIGNER.AFPADLSSRC.F1
- sql14.dts.designer.afpadlssrc.f1
ms.assetid: f9c3311f-7316-48d6-bf10-d810e70b4304
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: a5ec780327f12a4d81063c155aa5d3666b004ea6
ms.sourcegitcommit: 6443f9a281904af93f0f5b78760b1c68901b7b8d
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/11/2018
ms.locfileid: "53210153"
---
# <a name="azure-data-lake-store-source"></a>Источник Azure Data Lake Store
  Компонент **Источник Azure Data Lake Store** позволяет пакету служб SSIS считывать данные из Azure Data Lake Store. Поддерживаемые форматы файлов: текстовые и Avro.
  
 Компонент **Источник Azure Data Lake Store** входит в состав [пакета дополнительных компонентов SQL Server Integration Services (SSIS) для Azure](../../integration-services/azure-feature-pack-for-integration-services-ssis.md).  
  
> [!NOTE]
> Чтобы диспетчер подключений Azure Data Lake Store и компоненты, которые его используют (т. е. источник и цель Azure Data Lake Store), могли подключаться к службам, убедитесь, что вы скачали последнюю версию пакета дополнительных компонентов Azure [здесь](https://www.microsoft.com/download/details.aspx?id=49492). 
  
## <a name="configure-the-azure-data-lake-store-source"></a>Настройка источника Azure Data Lake Store
 1. Чтобы отобразить редактор для источника Azure Data Lake Store, перетащите компонент **Источник Azure Data Lake Store** в конструктор потока данных и дважды щелкните его, чтобы открыть редактор.  
  
2.  В поле **Диспетчер подключений Azure Data Lake Store** укажите существующий диспетчер подключений Azure Data Lake Store или создайте новый диспетчер, который ссылается на службу Azure Data Lake Store.  
  
    1.  В поле **Путь к файлу** укажите путь к исходному файлу в Azure Data Lake Store.   
  
    2.  В поле **Формат файла** укажите формат исходного файла.  
  
        Если формат файла — "Текст", необходимо указать значение **символа-разделителя столбцов** . Также выберите **Имена столбцов в первой строке данных** , если первая строка файла содержит имена столбцов.  
  
3.  После указания сведений о соединении переключитесь на страницу **Столбцы** , чтобы сопоставить столбцы источника со столбцами назначения для потока данных служб SSIS.   

## <a name="text-qualifier"></a>Ограничитель текста

**Источник Azure Data Lake Storage** не поддерживает квалификатор текста. Если вам нужно указать квалификатор текста для корректной обработки файлов, попробуйте скачать файлы на локальный компьютер и обработать их с помощью **источника "Неструктурированный файл"**. Источник "Неструктурированный файл" позволяет указать квалификатор текста. Дополнительные сведения: [Источник "Неструктурированный файл"](flat-file-source.md).
