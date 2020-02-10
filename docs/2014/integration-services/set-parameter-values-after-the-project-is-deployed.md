---
title: Установка значений параметров после развертывания проекта | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: c9dcca4d-f1a0-45ec-b078-f4d372589baf
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 910de9d388e60ae3664153e2f6cb3bb5203b289c
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "66055776"
---
# <a name="set-parameter-values-after-the-project-is-deployed"></a>Задать значения параметров после развертывания проекта
  Мастер развертывания позволяет задавать значения параметров по умолчанию сервера при развертывании проекта в каталог. После развертывания проекта в каталог задать значения по умолчанию сервера можно будет с помощью обозревателя объектов среды SQL Server Management Studio (SSMS) или Transact-SQL.  
  
### <a name="to-set-server-defaults-with-ssms-object-explorer"></a>Установка параметры по умолчанию сервера с помощью обозревателя объектов SSMS  
  
1.  Выберите и щелкните правой кнопкой мыши проект в узле **Службы Integration Services** .  
  
2.  Выберите пункт **Свойства** , чтобы открыть диалоговое окно **Свойства проекта** .  
  
3.  Откройте страницу «Параметры», нажав кнопку **Параметры** в разделе **Выбор страницы**.  
  
4.  Выберите нужный параметр в списке **Параметры** . Примечание. Столбец **Контейнер** помогает отличить параметры проекта от параметров пакета.  
  
5.  В столбце **Значение** укажите необходимое значение параметра по умолчанию сервера.  
  
 Чтобы установить параметры по умолчанию сервера с использованием Transact-SQL, используйте хранимую процедуру [catalog.set_object_parameter_value (база данных SSISDB)](/sql/integration-services/system-stored-procedures/catalog-set-object-parameter-value-ssisdb-database). Для просмотра текущих значений по умолчанию сервера используйте запрос к представлению [catalog.object_parameters (база данных SSISDB)](/sql/integration-services/system-views/catalog-object-parameters-ssisdb-database). Чтобы удалить значение по умолчанию сервера, используйте хранимую процедуру, используйте хранимую процедуру [catalog.clear_object_parameter_value (база данных SSISDB)](/sql/integration-services/system-stored-procedures/catalog-clear-object-parameter-value-ssisdb-database).  
  
## <a name="see-also"></a>См. также:  
 [Integration Services параметры &#40;служб SSIS&#41;](integration-services-ssis-package-and-project-parameters.md)  
  
  
