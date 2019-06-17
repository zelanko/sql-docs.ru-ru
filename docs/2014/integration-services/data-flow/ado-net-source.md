---
title: Источник ADO NET | Документы Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.adonetsource.f1
helpviewer_keywords:
- ADO.NET source
- sources [Integration Services], ADO.NET
- sources [Integration Services], DataReader
- .NET Framework [Integration Services]
- DataReader source
ms.assetid: 2a2f1750-2cda-4dda-9dca-623a96a6b3c0
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 1bc6c150f8c8f4f4e6f68b275a901ab8f1f5e8e5
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "62832487"
---
# <a name="ado-net-source"></a>Источник ADO NET
  Источник ADO NET использует данные поставщика .NET и делает данные доступными для потока данных.  
  
 Вы можете использовать источник ADO NET для подключения к [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]. Соединение с базой данных [!INCLUDE[ssSDS](../../includes/sssds-md.md)] с помощью OLE DB не поддерживается. Дополнительные сведения о [!INCLUDE[ssSDS](../../includes/sssds-md.md)]см. в разделе [Общие рекомендации и ограничения (база данных SQL Windows Azure)](https://go.microsoft.com/fwlink/?LinkId=248228).  
  
## <a name="data-type-support"></a>Поддержка типов данных  
 Источник преобразует все типы данных, которые не сопоставлены с конкретными типами данных служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] , в тип данных служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] DT_NTEXT. Преобразованию подвергаются даже данные типа `System.Object`.  
  
 Тип данных DT_NTEXT можно изменить на тип DT_WSTR, а DT_WSTR на DT_NTEXT. Типы данных меняются установкой свойства **DataType** в диалоговом окне **Расширенный редактор** источника ADO NET. Дополнительные сведения см. в статье [Common Properties](../common-properties.md).  
  
 Тип данных DT_NTEXT можно также преобразовать в типы DT_BYTES и DT_STR с помощью преобразования «Конвертация данных» после источника ADO NET. Дополнительные сведения см. в статье [Data Conversion Transformation](transformations/data-conversion-transformation.md).  
  
 В службах [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]типы данных для обозначения дат (DT_DBDATE, DT_DBTIME2, DT_DBTIMESTAMP2 и DT_DBTIMESTAMPOFFSET) соответствуют определенным типам данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Источник ADO NET можно настроить на преобразование типов данных даты, используемых [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , в типы, используемые службами [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] . Чтобы настроить источник ADO NET на преобразование типов данных «date», задайте для свойства **Версия системы типов** диспетчера соединений значение [!INCLUDE[vstecado](../../includes/vstecado-md.md)] или **Последняя**. (Свойство **Версия системы типов** находится на странице **Все** диалогового окна **Диспетчер соединений** . Чтобы открыть диалоговое окно **Диспетчер соединений** , щелкните правой кнопкой мыши диспетчер соединений [!INCLUDE[vstecado](../../includes/vstecado-md.md)] и выберите команду **Изменить**.)  
  
> [!NOTE]  
>  Если свойство **Версия системы типов** диспетчера соединений [!INCLUDE[vstecado](../../includes/vstecado-md.md)] равно **SQL Server 2005**, система преобразует типы данных даты [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] в DT_WSTR.  
  
 Система преобразует определяемые пользователем типы данных в объекты BLOB служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] , если поставщик в диспетчере соединений [!INCLUDE[vstecado](../../includes/vstecado-md.md)] указан как поставщик данных .NET для [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (SqlClient). При преобразовании определяемых пользователем типов данных система применяет следующие правила.  
  
-   Если данные не являются большим определяемым пользователем типом, система преобразует данные в тип DT_BYTES.  
  
-   Если данные не являются большим определяемым пользователем типом и свойство **Длина** столбца базы данных равно -1 или его величина превышает 8000 байт, система преобразует эти данные в тип DT_IMAGE.  
  
-   Если данные являются большим определяемым пользователем типом, система преобразует их в тип DT_IMAGE.  
  
    > [!NOTE]  
    >  Если источник ADO NET не настроен для использования вывода ошибок на выходе, система передает данные столбцу DT_IMAGE в виде потока фрагментами по 8000 байт. Если источник ADO NET настроен для использования вывода ошибок на выходе, система передает весь массив байтов столбцу DT_IMAGE. Дополнительные сведения о настройке компонентов для использования вывода ошибок на выходе см. в разделе [Обработка ошибок в данных](error-handling-in-data.md).  
  
 Дополнительные сведения о типах данных служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] , поддерживаемых преобразованиях и сопоставлении типов данных в различных базах данных, в том числе в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], см. в разделе [Типы данных служб Integration Services](integration-services-data-types.md).  
  
 Дополнительные сведения о сопоставлении типов данных [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] с управляемыми типами данных см. в разделе [Работа с типами данных в потоке данных](../extending-packages-custom-objects/data-flow/working-with-data-types-in-the-data-flow.md).  
  
## <a name="ado-net-source-troubleshooting"></a>Устранение неполадок источника ADO NET  
 Можно протоколировать вызовы, сделанные источником ADO NET к внешним поставщикам данных. Эта возможность ведения журнала может быть использована для устранения неполадок загрузки данных из внешнего источника, выполняемой источником ADO NET. Чтобы протоколировать вызовы источника ADO NET к внешнему поставщику данных, необходимо разрешить ведение журнала пакета и выбрать событие **Диагностика** на уровне пакета. Дополнительные сведения см. в разделе [Инструменты устранения неполадок при выполнении пакетов](../troubleshooting/troubleshooting-tools-for-package-execution.md).  
  
## <a name="ado-net-source-configuration"></a>Настройка источника ADO NET  
 Источник ADO NET настраивается предоставлением инструкции SQL, которая определяет результирующий набор. Например, источник ADO NET, который подключается к базе данных [!INCLUDE[ssSampleDBUserInputNonLocal](../../includes/sssampledbuserinputnonlocal-md.md)] и использует инструкцию SQL `SELECT * FROM Production.Product` , извлекает все строки из таблицы **Production.Product** и предоставляет набор данных для нисходящего компонента.  
  
> [!NOTE]  
>  Когда инструкция SQL используется для вызова хранимой процедуры, возвращающей результаты из временной таблицы, используйте параметр WITH RESULT SETS для определения метаданных набора результатов.  
  
> [!NOTE]  
>  Если при использовании инструкции SQL для выполнения хранимой процедуры происходит сбой пакета со следующей ошибкой, эту ошибку можно исправить путем добавления инструкции `SET FMTONLY OFF` перед инструкцией EXEC.  
>   
>  **Столбец <имя_столбца> не найден в источнике данных.**  
  
 Источник ADO NET использует диспетчер соединений [!INCLUDE[vstecado](../../includes/vstecado-md.md)] для подключения к источнику данных, а диспетчер соединений указывает поставщика .NET. Дополнительные сведения см. в статье [ADO.NET Connection Manager](../connection-manager/ado-net-connection-manager.md).  
  
 Источник ADO NET имеет один обычный выход и один выход ошибок.  
  
 Значения свойств можно задавать с помощью конструктора [!INCLUDE[ssIS](../../includes/ssis-md.md)] или программными средствами.  
  
 Дополнительные сведения о свойствах, которые вы можете задать в диалоговом окне **Расширенный редактор** или программными средствами, см. в следующих разделах.  
  
-   [Common Properties](../common-properties.md)  
  
-   [Пользовательские свойства ADO NET](ado-net-custom-properties.md)  
  
 Дополнительные сведения о настройке свойств см. в разделе [Установление свойств компонента потока данных](set-the-properties-of-a-data-flow-component.md).  
  
## <a name="see-also"></a>См. также  
 [Назначение DataReader](datareader-destination.md)   
 [Назначение «ADO.NET»](ado-net-destination.md)   
 [Поток данных](data-flow.md)  
  
  
