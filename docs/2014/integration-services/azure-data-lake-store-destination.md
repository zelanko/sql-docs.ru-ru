---
title: Цель Azure Data Lake Store | Документы Майкрософт
ms.custom: ''
ms.date: 06/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- integration-services
ms.topic: conceptual
f1_keywords:
- SQL12.DTS.DESIGNER.AFPADLSDEST.F1
- SQL11.DTS.DESIGNER.AFPADLSDEST.F1
ms.assetid: d0e86032-2a6b-48b2-898f-e94328474fde
author: yualan
ms.author: janinez
manager: craigg
ms.openlocfilehash: 2f10f78f59a6ec1dd5d5119a89624295935d6ff9
ms.sourcegitcommit: 5a8678bf85f65be590676745a7fe4fcbcc47e83d
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/22/2019
ms.locfileid: "58382499"
---
# <a name="azure-data-lake-store-destination"></a>Цель Azure Data Lake Store
  Компонент **Цель Azure Data Lake Store** позволяет пакету служб SSIS записывать данные в Azure Data Lake Store. Поддерживаемые форматы файлов: текстовые, Avro и ORC. 
  
## <a name="configure-the-azure-data-lake-store-destination"></a>Настройка цели Azure Data Lake Store 

1. Перетащите компонент **Цель Azure Data Lake Store** в конструктор потока данных и дважды щелкните его, чтобы открыть редактор.  

2.  В поле **Диспетчер подключений Azure Data Lake Store** укажите существующий диспетчер подключений Azure Data Lake Store или создайте новый диспетчер, который ссылается на службу Azure Data Lake Store.  
  
    1.  В поле **Путь к файлу** укажите имя файла, в который требуется записать данные. Если этот файл уже существует, его содержимое будет перезаписано.  
  
    2.  В поле **Формат файла** укажите формат файла, который следует использовать.  
  
        Если формат файла — "Текст", необходимо указать значение **символа-разделителя столбцов** . Также выберите **Имена столбцов в первой строке данных** , если первая строка файла содержит имена столбцов.  

        Если формат файла — ORC, вам потребуется установить JRE соответствующей платформы. 
  
3.  После указания сведений о соединении переключитесь на страницу **Столбцы** , чтобы сопоставить столбцы источника со столбцами назначения для потока данных служб SSIS.  
