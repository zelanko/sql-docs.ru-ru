---
title: Цель Azure Data Lake Store | Документы Майкрософт
ms.custom: ''
ms.date: 06/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- SQL12.DTS.DESIGNER.AFPADLSDEST.F1
- SQL11.DTS.DESIGNER.AFPADLSDEST.F1
ms.assetid: d0e86032-2a6b-48b2-898f-e94328474fde
author: yualan
ms.author: janinez
manager: craigg
ms.openlocfilehash: ebf686807169bb850e5a3ae8fac8cfb0b8ca7791
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2020
ms.locfileid: "66061460"
---
# <a name="azure-data-lake-store-destination"></a>Цель Azure Data Lake Store
  Компонент **Цель Azure Data Lake Store** позволяет пакету служб SSIS записывать данные в Azure Data Lake Store. Поддерживаются следующие форматы файлов: текст, AVRO и ORC. 
  
## <a name="configure-the-azure-data-lake-store-destination"></a>Настройка цели Azure Data Lake Store 

1. Перетащите компонент **Цель Azure Data Lake Store** в конструктор потока данных и дважды щелкните его, чтобы открыть редактор.  

2.  В поле **Диспетчер подключений Azure Data Lake Store** укажите существующий диспетчер подключений Azure Data Lake Store или создайте новый диспетчер, который ссылается на службу Azure Data Lake Store.  
  
    1.  В поле **Путь к файлу** укажите имя файла, в который требуется записать данные. Если этот файл уже существует, его содержимое будет перезаписано.  
  
    2.  В поле **Формат файла** укажите формат файла, который следует использовать.  
  
        Если формат файла — "Текст", необходимо указать значение **символа-разделителя столбцов** . Также выберите **имена столбцов в первой строке данных** , если первая строка в файле содержит имена столбцов.  

        Если формат файла — ORC, вам потребуется установить JRE соответствующей платформы. 
  
3.  После указания сведений о соединении переключитесь на страницу **Столбцы** , чтобы сопоставить столбцы источника со столбцами назначения для потока данных служб SSIS.  
