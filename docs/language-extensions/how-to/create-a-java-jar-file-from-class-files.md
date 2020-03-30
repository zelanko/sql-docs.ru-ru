---
title: Создание JAR-файла Java из файлов класса
description: Узнайте, как создать JAR-файл Java из файлов класса
author: dphansen
ms.author: davidph
ms.date: 11/05/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: language-extensions
monikerRange: '>=sql-server-ver15||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: e5a53eb4b8da04a799461dcb1e0cb32feff2fe6f
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/29/2020
ms.locfileid: "73658865"
---
# <a name="create-a-java-jar-file-from-class-files"></a>Создание JAR-файла Java из файлов класса
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

Сведения о том, как упаковывать файлы класса в JAR-файл при использовании [расширений языка SQL Server](../language-extensions-overview.md) для выполнения кода Java. Рекомендуется упаковывать файлы.

## <a name="create-a-jar-file"></a>Создание JAR-файла

Чтобы создать JAR-файл из файлов класса, перейдите в папку с файлом класса и выполните следующую команду:

```cmd
jar -cf <MyJar.jar> *.class
```

Убедитесь, что путь к `jar.exe` включен в системную переменную PATH. Либо укажите полный путь к этому файлу, который расположен в подпапке `/bin` папки JDK. Пример:

```cmd
C:\Users\MyUser\Desktop\jdk1.8.0_201\bin\jar -cf <MyJar.jar> *.class
```

## <a name="next-steps"></a>Дальнейшие действия

+ [Вызов среды выполнения Java в расширениях языка SQL Server](../how-to/call-java-from-sql.md)