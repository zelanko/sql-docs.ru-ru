---
title: Настройка значений параметров после развертывания проекта | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- integration-services
ms.topic: conceptual
ms.assetid: c9dcca4d-f1a0-45ec-b078-f4d372589baf
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: f5e7248868a368ee0ea956b46b63c9c8d024393b
ms.sourcegitcommit: 5a8678bf85f65be590676745a7fe4fcbcc47e83d
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/22/2019
ms.locfileid: "58379932"
---
# <a name="set-parameter-values-after-the-project-is-deployed"></a>Задать значения параметров после развертывания проекта
  Мастер развертывания позволяет задавать значения параметров по умолчанию сервера при развертывании проекта в каталог. После развертывания проекта в каталог задать значения по умолчанию сервера можно будет с помощью обозревателя объектов среды SQL Server Management Studio (SSMS) или Transact-SQL.  
  
### <a name="to-set-server-defaults-with-ssms-object-explorer"></a>Установка параметры по умолчанию сервера с помощью обозревателя объектов SSMS  
  
1.  Выберите и щелкните правой кнопкой мыши проект в узле **Службы Integration Services** .  
  
2.  Выберите пункт **Свойства** , чтобы открыть диалоговое окно **Свойства проекта** .  
  
3.  Откройте страницу «Параметры», нажав кнопку **Параметры** в разделе **Выбор страницы**.  
  
4.  Выберите нужный параметр в списке **Параметры** . Примечание. **Контейнера** столбец помогает отличить параметры проекта от параметров пакета.  
  
5.  В столбце **Значение** укажите необходимое значение параметра по умолчанию сервера.  
  
 Чтобы установить параметры по умолчанию сервера с использованием Transact-SQL, используйте хранимую процедуру [catalog.set_object_parameter_value (база данных SSISDB)](/sql/integration-services/system-stored-procedures/catalog-set-object-parameter-value-ssisdb-database). Для просмотра текущих значений по умолчанию сервера используйте запрос к представлению [catalog.object_parameters (база данных SSISDB)](/sql/integration-services/system-views/catalog-object-parameters-ssisdb-database). Чтобы удалить значение по умолчанию сервера, используйте хранимую процедуру, используйте хранимую процедуру [catalog.clear_object_parameter_value (база данных SSISDB)](/sql/integration-services/system-stored-procedures/catalog-clear-object-parameter-value-ssisdb-database).  
  
## <a name="see-also"></a>См. также  
 [Службы Integration Services &#40;SSIS&#41; параметров](integration-services-ssis-package-and-project-parameters.md)  
  
  
