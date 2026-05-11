# KNK Persian CV

**KNK Persian CV** is a fully Persian-ready résumé template, derived from the original **YAAC: Another Awesome CV**.  
It was first based on a CV template from Alessandro Plasmati, then adapted to support the Persian language and right‑to‑left scripts.  
The template uses _XeLaTeX_ and a combination of Persian and Latin fonts (Vazirmatn for Persian, Source Sans Pro for Latin).  
_[Font Awesome](http://fontawesome.io/)_ icons highlight important elements.

All layout logic resides in the class file `knk-persian-cv.cls`, keeping the document body clean and easy to customise.

> **⚠️ All personal data, company names, university names, project titles, and contact details shown in the examples are mock data provided for demonstration purposes only. You should replace them with your own real information.**

More information about the original Alessandro Plasmati template can be found here:

   - [Scribd](http://fr.scribd.com/doc/16335667/Writing-your-Professional-CV-with-LaTeX)
   - [LaTeX Templates](http://www.latextemplates.com/template/plasmati-graduate-cv)
   - [ShareLatex](https://www.sharelatex.com/templates/cv-or-resume/professional-cv)

## Preview

### Alternative style

| Page 1 | Page 2 |
|:---:|:---:|
| ![Résumé](example/preview/cv1-alternative.jpeg) | ![Résumé](example/preview/cv2-alternative.jpeg) |

## How to use **KNK Persian CV** LaTeX class

### Use the **KNK Persian CV** options

When declaring `\documentclass` you can use one or more options to customise your CV:

1. **localFont** – use the fonts included in the `fonts` folder.
2. **alternative** – use the alternative header layout.
3. **10pt**, **11pt** or **12pt** – change the base font size.
4. **compact** – reduce vertical space between experience entries.

```latex
% Default (traditional header, system fonts, blue colour scheme)
\documentclass{knk-persian-cv}

% Use local fonts, traditional header
\documentclass[localFont]{knk-persian-cv}

% Alternative header, system fonts
\documentclass[alternative]{knk-persian-cv}

% All together
\documentclass[localFont,alternative,10pt]{knk-persian-cv}

% Compact layout
\documentclass[compact]{knk-persian-cv}

### Construct the header

Outside the `\socialinfo` wrapper you must define `\name` and `\tagline`.

```latex
% Persian mock data
\name{سامان}{نیک‌فر}
\tagline{مهندس داده}

% Optional photo
\photo[circular]{2.5cm}{avatar}

\socialinfo{
  \linkedin{samannikfar}
  \github{saman-nik}\\
  \smartphone{\lr{+98 912 345 6789}}
  \email{saman.nikfar@mail.com}\\
  \address{ایران، تهران}
}
```

Use `\makecvheader` to generate the header.

```latex
\makecvheader
```

### Set the left column size

Sections share a left column width (2.5 cm by default). Change it with:

```latex
\setleftcolumnlength{2cm}
```

### Construct the *competences* (skills) section

Skills are shown as keyword lists.

```latex
\begin{keywords}
    \keywordsentry{برنامه‌نویسی}{پایتون، R، Java، SQL}
    \keywordsentry{یادگیری ماشین}{TensorFlow, PyTorch, Scikit‑Learn}
    \keywordsentry{مهندسی داده}{Apache Spark, Hadoop, Airflow}
\end{keywords}
```

### Construct the *experiences* section

First declare the `experiences` environment, then use `\experience` and `\consultantexperience`.

```latex
\begin{experiences}
  \experience
    {اکنون}   {راهبر تیم علوم داده}{شرکت نوآوران داده‌پرداز پارس}{تهران}
    {مهر ۱۴۰۰} {
      \begin{itemize}
        \item طراحی سیستم توصیه‌گر \lr{(Recommender System)} منجر به افزایش ۱۲٪ فروش.
        \item رهبری تیم ۴ نفره داده در متدولوژی \lr{Agile/Scrum}.
      \end{itemize}
    }
    {Python, Spark, TensorFlow, Kubernetes}
  \emptySeparator

  \experience
    {شهریور ۱۴۰۰} {مهندس یادگیری ماشین}{شرکت توسعه فناوری آریا}{تهران}
    {فروردین ۱۳۹۷} {
      \begin{itemize}
        \item توسعه مدل پیش‌بینی ریزش مشتری با دقت ۸۲٪.
        \item ساخت داشبوردهای مدیریتی با \lr{Tableau}.
      \end{itemize}
    }
    {Python, Scikit-Learn, SQL, Docker}
\end{experiences}
```

### Construct the *languages* section

```latex
\begin{skills}
    \skill{فارسی}{5}
    \skill{انگلیسی}{4}
    \skill{آلمانی}{3}
\end{skills}
```

### Construct the *scholarship* section

```latex
\begin{scholarship}
  \scholarshipentry{۱۳۹۸}
    {کارشناسی ارشد مهندسی داده، \textbf{دانشگاه فناوری‌های هوشمند تهران}}
  \scholarshipentry{۱۳۹۵}
    {کارشناسی مهندسی کامپیوتر، \textbf{دانشگاه تهران}}
\end{scholarship}
```

### Construct the *projects* section

```latex
\begin{projects}
  \project
    {سامانه تشخیص ناهنجاری در شبکه‌های اجتماعی}{۱۴۰۱ - ۱۴۰۲}
    {\github{samannikfar/anomaly-social}}
    {طراحی پلتفرم متن‌باز برای تشخیص آنومالی در شبکه‌های اجتماعی به صورت \lr{Real-time}.}
    {Python, Kafka, PyTorch, Elasticsearch}
\end{projects}
```

### Construct the *certifications* section

Use the `\certificate` command to list your credentials.

```latex
\begin{certifications}
  \certificate
    {یادگیری ماشین}
    {Coursera (Stanford)}
    {https://coursera.org/verify/mock123}
    {۱۴۰۱}

  \certificate
    {مدیریت پروژه حرفه‌ای}
    {PMI}
    {https://pmi.org/verify/mock456}
    {۱۴۰۰}
\end{certifications}
```

### Construct the *references* section

```latex
\begin{referees}
  \referee
    {دکتر مریم رضوی}
    {استاد دانشکده کامپیوتر}
    {دانشگاه صنعتی شریف}
    {m.razavi@sharif.edu}
    {\lr{+98 21 66166000}}

  \refereeMailOnly
    {مهندس امیرحسین کریمی}
    {مدیر فنی \lr{(CTO)}}
    {شرکت نوآوران داده‌پرداز پارس}
    {a.karimi@dpi-co.ir}
\end{referees}
```

### Construct the *publications* section

```latex
\begin{LTR}
    \setLTRbibitems
    \resetlatinfont
    \nocite{*}
    \printbibliography[heading=none]
\end{LTR}
```

## License

The LaTeX class file _yaac-another-awesome-cv_ is published under the [LPPL Version 1.3c](https://www.latex-project.org/lppl.txt).  
All content files are published under the [CC BY-SA 4.0 License](https://creativecommons.org/licenses/by-sa/4.0/legalcode).
```
