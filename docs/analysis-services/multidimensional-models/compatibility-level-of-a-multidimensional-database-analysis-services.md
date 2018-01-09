---
title: "Уровень совместимости многомерной базы данных (службы Analysis Services) | Документы Microsoft"
ms.custom: 
ms.date: 03/04/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: data-mining
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 978279e6-a581-4184-af9d-8701b9826a89
caps.latest.revision: "18"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: f0b002ac618a9e55da3a433c11817eca716345ef
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/08/2018
---
# <a name="compatibility-level-of-a-multidimensional-database-analysis-services"></a>Уровень совместимости многомерной базы данных (службы Analysis Services)
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]В [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], свойство уровня совместимости базы данных определяет функциональный уровень базы данных. Уровень совместимости уникален для каждого типа модели. Например, для многомерной и табличной баз данных уровень совместимости **1100** имеет разное значение.  
  
 Этот раздел описывает уровень совместимости только для многомерных баз данных. Дополнительные сведения о табличных решениях см. в разделе [Уровень совместимости табличных моделей в службах Analysis Services](../../analysis-services/tabular-models/compatibility-level-for-tabular-models-in-analysis-services.md).  
  
> [!NOTE]  
>  Табличные модели имеют дополнительные уровни совместимости базы данных, неприменимые к многомерным моделям. Для многомерных моделей уровень совместимости **1103** не существует. См. раздел [What is new for the Tabular model in SQL Server 2012 SP1 and compatibility level](http://go.microsoft.com/fwlink/?LinkId=301727) (Новые возможности табличных моделей в SQL Server 2012 с пакетом обновления 1 (SP1) и уровень совместимости), где приведены дополнительные сведения о **1103** для табличных решений.  
  
 **Уровень совместимости для многомерных баз данных**  
  
 В настоящее время единственной особенностью многомерных баз данных, зависящей от функционального уровня, является архитектура хранилища строк. Поднимая уровень совместимости базы данных, можно переопределить максимальный предел в 4 ГБ для хранилища строк с мерами и измерениями.  
  
 Для многомерной базы данных допустимы следующие значения для свойства **CompatibilityLevel** :  
  
|Настройка|Description|  
|-------------|-----------------|  
|**1050**|Это значение недоступно в скриптах и инструментах, но соответствует базам данных, созданным в [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)], [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]или [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]. Любая база данных, в которой значение **CompatibilityLevel** явным образом не задано, неявно работает на уровне **1050** .|  
|**1100**|Это значение по умолчанию для новых баз данных, созданных в [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] или [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]. К тому же его можно задавать для баз данных, созданных в более ранних версиях служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] , чтобы разрешить использование функций, которые поддерживаются только на этом уровне совместимости, а именно увеличенного хранилища строк для атрибутов измерений или мер числа различных объектов, содержащих строковые данные.<br /><br /> Базы данных, для которых **CompatibilityLevel** имеет значение **1100** , получают дополнительное свойство, **StringStoresCompatibilityLevel**. Оно позволяет выбрать другое хранилище строк для измерений и секций.|  
  
> [!WARNING]  
>  Повышение уровня совместимости базы данных необратимо. После повышения уровня совместимости до **1100**работу с базой данных необходимо продолжать на более новых серверах. Выполнить откат до уровня **1050**нельзя. Присоединить или восстановить базу данных с уровнем совместимости **1100** на сервере, версия которого ниже [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] или [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], нельзя.  
  
## <a name="prerequisites"></a>предварительные требования  
 Уровни совместимости баз данных введены в [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]. Для просмотра или установки уровня совместимости базы данных необходимо наличие служб [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)][!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] или боле поздней версии.  
  
 База данных не может быть локальным кубом. Локальные кубы не поддерживают свойство **CompatibilityLevel** .  
  
 База данных должна быть создана в предыдущем выпуске (SQL Server 2008 R2 или более раннем), затем присоединена или восстановлена на сервере [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)][!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] или боле поздней версии с версии. Базы данных, развернутые в SQL Server 2012, уже на уровне **1100** и не могут быть понижены для выполнения на более низком уровне.  
  
## <a name="determine-the-existing-database-compatibility-level-for-a-multidimensional-database"></a>Определите существующий уровень совместимости базы данных для многомерной базы данных  
 Существует только один способ просмотреть или изменить уровень совместимости базы данных — посредством XMLA. Можно просмотреть или изменить скрипт XML для аналитики, указывающий базу данных в SQL Server Management Studio.  
  
 Если поиск определения XMLA базы данных на наличие свойства **CompatibilityLevel** показывает, что последнее не существует, вероятнее всего, база данных находится на уровне **1050** .  
  
 Инструкции по просмотру и изменению скрипта XMLA даны в следующем разделе.  
  
## <a name="set-the-database-compatibility-level-in-sql-server-management-studio"></a>Установка уровня совместимости базы данных в среде SQL Server Management Studio  
  
1.  Прежде чем повысить уровень совместимости, сделайте резервную копию базы данных на тот случай, если потребуется отменить изменения позже.  
  
2.  В SQL Server Management Studio подключитесь к серверу [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)][!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] , на котором размещена база данных.  
  
3.  Щелкните правой кнопкой мыши имя базы данных, наведите указатель на команду **Создать скрипт для базы данных**, затем на команду **Используя ALTER**и выберите **В новом окне редактора запросов**. В новом окне откроется XMLA-представление базы данных.  
  
4.  Скопируйте следующий XML-элемент:  
  
    ```  
    <ddl200:CompatibilityLevel>1100</ddl200:CompatibilityLevel>  
    ```  
  
5.  Вставьте его после закрывающего элемента `</Annotations>` , но перед элементом `<Language>` . Код XML должен выглядеть, как в следующем примере:  
  
    ```  
    </Annotations>  
    <ddl200:CompatibilityLevel>1100</ddl200:CompatibilityLevel>  
    <Language>1033</Language>  
    ```  
  
6.  Сохраните файл.  
  
7.  Чтобы выполнить скрипт, выберите пункт **Выполнить** в меню "Запрос" или нажмите клавишу F5.  
  
## <a name="supported-operations-that-require-the-same-compatibility-level"></a>Поддерживаемые операции, требующие такого же уровня совместимости  
 Следующие операции требуют, чтобы у баз данных-источников был одинаковый уровень совместимости.  
  
1.  Слияние секций разных баз данных поддерживается, только если обе базы данных имеют одинаковый уровень совместимости.  
  
2.  Использование связанных измерений из другой базы данных требует одинакового уровня совместимости. Например, если вы хотите использовать связанное измерение из базы данных [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] в базе данных [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] , следует портировать базу данных [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] на сервер [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] и задать уровень совместимости **1100**.  
  
3.  Синхронизация серверов поддерживается только для серверов с одинаковой версией и уровнем совместимости баз данных.  
  
## <a name="next-steps"></a>Next Steps  
 После повышения уровня совместимости базы данных можно задать свойство **StringStoresCompatibilityLevel** в [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)]. Это увеличит строковое хранилище для измерений и мер. Дополнительные сведения об этой функции см. в разделе [Настройка хранилища строк для измерений и секций](../../analysis-services/multidimensional-models/configure-string-storage-for-dimensions-and-partitions.md).  
  
## <a name="see-also"></a>См. также:  
 [Резервное копирование, восстановление и синхронизация баз данных (XMLA)](../../analysis-services/multidimensional-models-scripting-language-assl-xmla/backing-up-restoring-and-synchronizing-databases-xmla.md)  
  
  
