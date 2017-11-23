---
title: "Начало работы с SSMA для консоли Oracle (OracleToSQL) | Документы Microsoft"
ms.prod: sql-non-specified
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: 
ms.technology: sql-ssma
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Oracle Console, Console Output Conventions
- Oracle Console, Launching Console
ms.assetid: 667a5e4a-6848-4973-a72d-1287f64718ac
caps.latest.revision: "31"
author: Shamikg
ms.author: Shamikg
manager: v-thobro
ms.workload: Inactive
ms.openlocfilehash: 35c34140f987d243648cd6172aa3a9a165c41f76
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/09/2017
---
# <a name="getting-started-with-ssma--for-oracle-console-oracletosql"></a>Начало работы с SSMA для консоли Oracle (OracleToSQL)
В этом разделе описывается, как запустить и приступить к работе с Oracle консольного приложения. Также перечислены в настоящем документе, соглашения используются в типичного окна вывода консоли SSMA.  
  
## <a name="launching-ssma-console"></a>При запуске консоли SSMA  
Чтобы запустить консольное приложение SSMA используйте следующие действия:  
  
1.  Последовательно выберите пункты **запустить** и пункты **все программы**.  
  
2.  Нажмите кнопку  **[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Migration Assistant для Oracle командной строки** ярлык.  
  
    Отображает меню использования консоли SSMA и `(/? Help)`, чтобы помочь вам приступить к работе с консольного приложения.  
  
## <a name="procedure-for-using-the-ssma-console"></a>Процедура использования консоли SSMA  
После консоль успешно запускается в среде Windows, можно выполнить следующие действия для работы с ней:  
  
1.  Настройка консоли SSMA через файлы скриптов. Дополнительные сведения об этом разделе см. в разделе [Создание файлов скриптов &#40; OracleToSQL &#41;](../../ssma/oracle/creating-script-files-oracletosql.md) .  
  
2.  [Создание файлов значение переменной &#40; OracleToSQL &#41;](../../ssma/oracle/creating-variable-value-files-oracletosql.md)  
  
3.  [Создание файлов подключения сервера &#40; OracleToSQL &#41;](../../ssma/oracle/creating-the-server-connection-files-oracletosql.md)  
  
4.  [Выполнение консоли SSMA &#40; OracleToSQL &#41; ](../../ssma/oracle/executing-the-ssma-console-oracletosql.md) зависимости от потребностей проекта  
  
Дополнительные функции:  
  
1.  [Укажите пароль](http://msdn.microsoft.com/en-us/8c7d9f8e-06bb-476c-bbd2-15b61d5bba3c) и экспортировать и импортировать его на других компьютерах окна  
  
2.  [Составление отчетов](http://msdn.microsoft.com/en-us/ccad6262-01e1-447a-bd2b-c105154c80ce) для просмотра xml подробный вывод отчетов для оценки миграции /conversion и данных. Подробные сведения об ошибке отчеты также можно создать для команд обновить и синхронизации.  
  
## <a name="ssma-console-output-conventions"></a>Соглашения о выходных данных консоли SSMA  
После выполнения команды сценария SSMA и параметры, консольная программа отображает результаты и сообщения (сведения, ошибка, т. д.) для пользователя на консоли или при необходимости перенаправляет выходные данные в XML-файл. Каждый тип сообщения в выводе обозначается уникальным цветом. Например текстовое сообщение в белый цвет обозначает команд файла скрипта; в зеленый цвет представляет запрос для ввода данных пользователем и т. д.  
  
![Вывод консоли ssma_oracle](../../ssma/db2/media/ssmaconsoleoutput_oracle.jpg "консоли ssma_oracle")  
  
Интерпретация цветовой выходные данные в консоли в следующей таблице:  
  
|Color|Description|  
|---------|---------------|  
|Красный|Неустранимая ошибка во время выполнения|  
|Серый|Метка даты и времени, сообщение для пользователя|  
|White|Файл команд, тип сообщения|  
|Желтый|Предупреждение|  
|Зеленый|Запрос для ввода данных пользователем|  
|Голубой|Начала, окончания и результат операции|  
  
## <a name="see-also"></a>См. также:  
[Установка SSMA для Oracle](http://msdn.microsoft.com/en-us/9211013a-ab24-4c52-9b26-87994b35e502)  
  
