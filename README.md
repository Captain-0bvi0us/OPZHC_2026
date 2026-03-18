# ОПЖЦ_2026 Семинар 11.03.2026.
##Задание для семинара по теме "Операторно-параметрические схемы имитационной модели"
##Козлов А.А. ИУ5-63Б

**Markdown с Mermaid**

flowchart TD
```mermaid
subgraph PRIBOR ["ОПС ПРИБОР"]
    direction TB
    title[<em>Блок ПРИБОР</em>]
    h1(["BPEMЯ=Tслом"]) ==> h2["сост:=<br>сломан"]
    h2 e11@==> h3(["режим=<br>работа"])
    h3 ==> h4(["мастер<br>=своб"])
    h4 ==> h5["мастер:=занят<br>Tрем:=funс(x)"]
    h5 e20@==> h6(["ВРЕМЯ=Трем"])
    h6 ==> h7["сост:=рабочий<br>мастер:=своб<br>Tслом:=func(x)"]
    h7 e10@==> h1

    h2 -.->par3((сост))
    h7 -.->par3
    par1((режим))-.->h3
    par2((мастер))-.->h4
    h5 -.->par2
    h7 -.->par2
    h5 -.->par4((Трем))
    par4 -.-> h6
    Ini@{shape: braces, label: "I::"} -.- h1
    HTf@{shape: braces, label: "I::Tслом = 100"}
end

subgraph MASTER ["ОПС МАСТЕР"]
    direction TB
    h11["режим:=отдых"] ==> h12(["ВРЕМЯ=Траб"])
    h12 ==> h13["режим:=работа<br>Тоtd:=func__"]
    h13 ==> h14(["ВРЕМЯ=Тоtd"])
    h14 ==> h18["Траб:=func__"]
    h18 ==> h15{"мастер<br>=..."}
    h15 ==>|"...= занят"| h16["Tрем:=Трем+<br>Траб-ВРЕМЯ"]
    h15 ==>|"...= своб"| h12
    h16 ==> h12

    par5((режим)) -.-> h11
    par5 -.-> h13
    par6((мастер)) -.-> h15
    h16 -.-> par7((Трем))
    InitM@{shape: braces, label: "i"} -.- h11
    TrabInit@{shape: braces, label: "Траб = 9ч"} -.- h12
end

%% Глобальные настройки стилей связей
e10@{ curve: linear}
e11@{ curve: natural}
e20@{ curve: stepAfter}

%% Классы раскраски
classDef cond fill:#bee,stroke:#aaa,stroke-width:1px,color:#000;
classDef state fill:#9e8,stroke:#333,stroke-width:1px,color:#000;
classDef navig fill:#eda,stroke:#333,stroke-width:1px,color:#000;

class h1,h3,h4,h6,h12,h14 cond;
class h2,h5,h7,h11,h13,h16,h18 state;
class h15 navig;

%% Стили узлов параметров и заголовка
style title fill:yellow,stroke:red,color:#000;
style par1 fill:#fcc,stroke:#111,stroke-width:2px,color:#000;
style par2 fill:#fae,stroke:#bbb,stroke-width:2px,color:#000;
style par4 fill:#ccc,stroke:#555,stroke-width:2px,color:#000;
style par5 fill:#fcc,stroke:#111,stroke-width:2px,color:#000;
style par6 fill:#fae,stroke:#bbb,stroke-width:2px,color:#000;
style par7 fill:#ccc,stroke:#555,stroke-width:2px,color:#000;

%% Клики для перехода по ссылкам (по заданию)
click par2 href "https://iu5.bmstu.ru" "переход для Мастера" _blank;
click par4 href "https://iu5.bmstu.ru" "переход к параметру" _blank;
```
