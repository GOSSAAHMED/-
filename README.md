!DOCTYPE html>
<html lang="ar" dir="rtl">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>الحساب الهرمي – Hierarchical Calculus</title>
  <style>
    * {
      box-sizing: border-box;
      margin: 0;
      padding: 0;
      font-family: system-ui, -apple-system, BlinkMacSystemFont, "Segoe UI", sans-serif;
    }

    body {
      background: #020617;
      color: #e5e7eb;
      line-height: 1.8;
    }

    a {
      color: inherit;
      text-decoration: none;
    }

    header {
      position: sticky;
      top: 0;
      z-index: 10;
      background: rgba(2, 6, 23, 0.95);
      backdrop-filter: blur(12px);
      border-bottom: 1px solid rgba(51, 65, 85, 1);
    }

    .container {
      max-width: 1150px;
      margin: 0 auto;
      padding: 0 1.25rem;
    }

    .nav {
      display: flex;
      justify-content: space-between;
      align-items: center;
      padding: 0.75rem 0;
      gap: 1rem;
    }

    .logo {
      font-weight: 800;
      font-size: 1.1rem;
      letter-spacing: 0.08em;
      color: #38bdf8;
      text-transform: uppercase;
    }

    .nav-links {
      display: flex;
      flex-wrap: wrap;
      gap: 0.75rem;
      font-size: 0.9rem;
    }

    .nav-links a {
      padding: 0.25rem 0.9rem;
      border-radius: 999px;
      border: 1px solid transparent;
      transition: background 0.2s ease, color 0.2s ease, border-color 0.2s ease;
      color: #cbd5f5;
    }

    .nav-links a:hover {
      background: #38bdf8;
      border-color: #38bdf8;
      color: #020617;
    }

    .lang-toggle {
      display: inline-flex;
      align-items: center;
      gap: 0.35rem;
      padding: 0.25rem 0.75rem;
      border-radius: 999px;
      border: 1px solid #64748b;
      font-size: 0.8rem;
      cursor: pointer;
      background: rgba(15, 23, 42, 0.9);
      color: #e5e7eb;
      white-space: nowrap;
    }

    .lang-toggle span {
      font-weight: 600;
    }

    main {
      padding-bottom: 3rem;
    }

    section {
      padding: 3rem 0;
      border-top: 1px solid rgba(15, 23, 42, 1);
    }

    .hero {
      padding-top: 3rem;
    }

    .hero-grid {
      display: grid;
      grid-template-columns: minmax(0, 2.1fr) minmax(0, 1.4fr);
      gap: 2.5rem;
      align-items: center;
    }

    .badge {
      display: inline-flex;
      align-items: center;
      gap: 0.4rem;
      padding: 0.2rem 0.8rem;
      border-radius: 999px;
      border: 1px solid rgba(148, 163, 184, 0.7);
      font-size: 0.8rem;
      color: #cbd5f5;
      margin-bottom: 1rem;
    }

    .badge-dot {
      width: 7px;
      height: 7px;
      border-radius: 999px;
      background: #22c55e;
    }

    .hero-title {
      font-size: 2.4rem;
      font-weight: 800;
      margin-bottom: 1rem;
    }

    .hero-title span {
      color: #38bdf8;
    }

    .hero-subtitle {
      font-size: 1.02rem;
      color: #cbd5f5;
      margin-bottom: 1.5rem;
    }

    .hero-actions {
      display: flex;
      flex-wrap: wrap;
      gap: 0.75rem;
      margin-bottom: 1.25rem;
    }

    .btn-primary,
    .btn-outline {
      padding: 0.6rem 1.4rem;
      border-radius: 999px;
      font-size: 0.92rem;
      border: 1px solid transparent;
      cursor: pointer;
      transition: background 0.2s ease, color 0.2s ease, border-color 0.2s ease;
      display: inline-flex;
      align-items: center;
      gap: 0.3rem;
    }

    .btn-primary {
      background: #38bdf8;
      color: #020617;
      border-color: #38bdf8;
      font-weight: 600;
    }

    .btn-primary:hover {
      background: #0ea5e9;
      border-color: #0ea5e9;
    }

    .btn-outline {
      background: transparent;
      color: #e5e7eb;
      border-color: #64748b;
    }

    .btn-outline:hover {
      background: rgba(148, 163, 184, 0.15);
    }

    .hero-note {
      font-size: 0.85rem;
      color: #94a3b8;
    }

    .hero-card {
      background:
        radial-gradient(circle at top, rgba(56, 189, 248, 0.18), transparent),
        rgba(15, 23, 42, 0.96);
      border-radius: 1.3rem;
      padding: 1.5rem;
      border: 1px solid rgba(148, 163, 184, 0.7);
      box-shadow: 0 24px 40px rgba(15, 23, 42, 0.9);
    }

    .hero-card-title {
      font-size: 1.05rem;
      font-weight: 600;
      margin-bottom: 0.8rem;
    }

    .formula-box {
      background: rgba(15, 23, 42, 0.96);
      border-radius: 0.9rem;
      padding: 1rem 1.2rem;
      border: 1px dashed rgba(148, 163, 184, 0.7);
      font-family: "Cascadia Code", "Consolas", ui-monospace, SFMono-Regular, Menlo, Monaco, monospace;
      font-size: 0.9rem;
      margin-bottom: 0.9rem;
      direction: ltr;
      text-align: left;
      color: #e5e7eb;
      overflow-x: auto;
    }

    .hero-card p {
      font-size: 0.9rem;
      color: #cbd5f5;
      margin-bottom: 0.6rem;
    }

    .section-title {
      font-size: 1.6rem;
      font-weight: 700;
      margin-bottom: 0.5rem;
    }

    .section-subtitle {
      font-size: 0.95rem;
      color: #9ca3af;
      margin-bottom: 1.5rem;
    }

    .grid-2 {
      display: grid;
      grid-template-columns: minmax(0, 1.3fr) minmax(0, 1fr);
      gap: 1.75rem;
    }

    .grid-3 {
      display: grid;
      grid-template-columns: repeat(3, minmax(0, 1fr));
      gap: 1.5rem;
    }

    .card {
      background: rgba(15, 23, 42, 0.96);
      border-radius: 1rem;
      padding: 1.25rem;
      border: 1px solid rgba(51, 65, 85, 1);
    }

    .card h3 {
      font-size: 1rem;
      margin-bottom: 0.6rem;
    }

    .card p {
      font-size: 0.9rem;
      color: #cbd5f5;
    }

    .list {
      list-style: none;
      margin-top: 0.4rem;
    }

    .list li {
      font-size: 0.9rem;
      color: #cbd5f5;
      margin-bottom: 0.35rem;
      padding-inline-start: 1rem;
      position: relative;
    }

    .list li::before {
      content: "•";
      position: absolute;
      inset-inline-start: 0;
      top: 0;
      color: #38bdf8;
    }

    .pill {
      display: inline-block;
      padding: 0.2rem 0.7rem;
      border-radius: 999px;
      border: 1px solid rgba(148, 163, 184, 0.6);
      font-size: 0.78rem;
      color: #cbd5f5;
      margin-bottom: 0.4rem;
    }

    .chapters-box {
      display: flex;
      flex-wrap: wrap;
      gap: 0.4rem;
      margin-top: 0.75rem;
    }

    .chap-pill {
      padding: 0.25rem 0.6rem;
      border-radius: 999px;
      background: rgba(15, 23, 42, 0.95);
      border: 1px dashed rgba(71, 85, 105, 1);
      font-size: 0.78rem;
      color: #e5e7eb;
    }

    .contact-box {
      background: rgba(15, 23, 42, 0.96);
      border-radius: 1rem;
      padding: 1.25rem;
      border: 1px solid rgba(51, 65, 85, 1);
      font-size: 0.9rem;
    }

    .contact-box a {
      color: #38bdf8;
      text-decoration: underline;
    }

    footer {
      border-top: 1px solid rgba(15, 23, 42, 1);
      padding: 1.5rem 0 2rem;
      font-size: 0.8rem;
      color: #9ca3af;
      text-align: center;
    }

    /* اللغة */
    .lang-en {
      display: none;
    }

    body.show-en {
      direction: ltr;
    }

    body.show-en .lang-en {
      display: block;
    }

    body.show-en .lang-ar {
      display: none;
    }

    body.show-en .nav-links {
      flex-direction: row-reverse;
    }

    body.show-en .nav-links a {
      margin-right: 0;
    }

    @media (max-width: 900px) {
      .hero-grid {
        grid-template-columns: minmax(0, 1fr);
      }
      .grid-2 {
        grid-template-columns: minmax(0, 1fr);
      }
      .grid-3 {
        grid-template-columns: minmax(0, 1fr);
      }
      .nav {
        flex-direction: column;
        align-items: flex-start;
      }
    }
  </style>
</head>
<body>
  <header>
    <div class="container">
      <nav class="nav">
        <div class="logo">
          <span class="lang-ar">الحساب الهرمي</span>
          <span class="lang-en">Hierarchical Calculus</span>
        </div>
        <div style="display:flex;align-items:center;gap:0.75rem;">
          <div class="nav-links">
            <a href="#overview">
              <span class="lang-ar">المقدمة</span>
              <span class="lang-en">Overview</span>
            </a>
            <a href="#theory">
              <span class="lang-ar">ما هو؟</span>
              <span class="lang-en">Theory</span>
            </a>
            <a href="#math">
              <span class="lang-ar">البنية الرياضية</span>
              <span class="lang-en">Math Structure</span>
            </a>
            <a href="#cosmos">
              <span class="lang-ar">هرم الكون</span>
              <span class="lang-en">Cosmic Hierarchy</span>
            </a>
            <a href="#library">
              <span class="lang-ar">المكتبة</span>
              <span class="lang-en">Library</span>
            </a>
            <a href="#contact">
              <span class="lang-ar">تواصل</span>
              <span class="lang-en">Contact</span>
            </a>
          </div>
          <button class="lang-toggle" id="langToggle" type="button">
            🌐 <span>AR</span> / EN
          </button>
        </div>
      </nav>
    </div>
  </header>

  <main>
    <!-- Hero / Overview -->
    <section id="overview" class="hero">
      <div class="container hero-grid">
        <div>
          <div class="badge lang-ar">
            <span class="badge-dot"></span>
            نظرية رياضية مقترحة – قيد التطوير
          </div>
          <div class="badge lang-en">
            <span class="badge-dot"></span>
            Proposed mathematical theory – in progress
          </div>

          <h1 class="hero-title lang-ar">
            الحساب <span>الهرمي</span><br />
            علم جديد فوق التفاضل الكلاسيكي.
          </h1>
          <h1 class="hero-title lang-en">
            <span>Hierarchical Calculus</span><br />
            A new layer beyond classical calculus.
          </h1>

          <p class="hero-subtitle lang-ar">
            هذا الموقع يقدّم الحساب الهرمي كطرح رياضي جديد موجّه للعلماء والباحثين.
            يهدف إلى تنظيم المشتقات في هرم مترابط: المشتق التفاضلي، النسبي،
            اللوغاريتمي، التتريشني، وما بعدها. العلم ليس جزءًا من المناهج
            التقليدية، بل يُقدَّم هنا كنظرية مفتوحة للنقاش والبحث.
          </p>
          <p class="hero-subtitle lang-en">
            This website introduces Hierarchical Calculus as a new mathematical proposal
            aimed at scientists and researchers. It organizes derivatives into a
            structured hierarchy: differential, relative, logarithmic, tetrational,
            and higher levels. The theory is not part of standard curricula and is
            presented here as an open framework for discussion and research.
          </p>

          <div class="hero-actions">
            <a href="#math" class="btn-primary">
              <span class="lang-ar">قراءة الأسس الرياضية</span>
              <span class="lang-en">Read the math foundations</span>
            </a>
            <a href="#new" class="btn-outline">
              <span class="lang-ar">لماذا هذا العلم جديد؟</span>
              <span class="lang-en">Why is this theory new?</span>
            </a>
          </div>

          <p class="hero-note lang-ar">
            ملاحظة: الحساب الهرمي هو طرح شخصي من تأليف أحمد أحمد، ولا يمثّل
            فرعًا رسميًا من الرياضيات حتى لحظة نشره هنا.
          </p>
          <p class="hero-note lang-en">
            Note: Hierarchical Calculus is a personal proposal authored by Ahmed Ahmed
            and is not yet a formal branch of mathematics in current academic programs.
          </p>
        </div>

        <aside class="hero-card">
          <h2 class="hero-card-title lang-ar">العلاقات الذهبية للمشتقات الهرمية</h2>
          <h2 class="hero-card-title lang-en">Golden relations of hierarchical derivatives</h2>

          <div class="formula-box">
            d₀ f(x) = f(x) · D₁ f(x)<br />
            f(x)^{D₂ f(x)} = x^{D₁ f(x)}<br />
            f(x) ↑↑ D₃ f(x) = x ↑↑ D₂ f(x)
          </div>

          <p class="lang-ar">
            تشكّل هذه العلاقات الذهبية العمود الفقري للحساب الهرمي، حيث تربط بين
            المشتق التفاضلي D₀، والنسبي D₁، واللوغاريتمي D₂، والتتريشني D₃ في
            نسق واحد، مع إمكانية التمديد لمستويات أعلى.
          </p>
          <p class="lang-en">
            These golden relations form the backbone of Hierarchical Calculus. They link
            the differential derivative D₀, the relative derivative D₁, the logarithmic
            derivative D₂, and the tetrational derivative D₃ in a single coherent
            structure, extendable to higher levels.
          </p>
        </aside>
      </div>
    </section>

    <!-- What is the theory -->
    <section id="theory">
      <div class="container">
        <h2 class="section-title lang-ar">ما هو الحساب الهرمي؟</h2>
        <h2 class="section-title lang-en">What is Hierarchical Calculus?</h2>

        <p class="section-subtitle lang-ar">
          الحساب الهرمي هو محاولة لتنظيم مفهوم المشتق في هرم من المستويات،
          بحيث يقابل كل مستوى اشتقاقي مستوى أعلى من العمليات على المتغيّر:
          من التفاضل العادي إلى النسب، ثم اللوغاريتم، ثم التتريشن، وهكذا.
        </p>
        <p class="section-subtitle lang-en">
          Hierarchical Calculus is an attempt to reorganize the concept of the derivative
          into a hierarchical tower of levels. Each derivative level corresponds to a higher
          operational layer on the variable: from classical differentiation to relative
          change, then logarithmic behavior, then tetration, and further.
        </p>

        <div class="grid-3">
          <div class="card">
            <h3 class="lang-ar">المستوى الأول: D₀ – المشتق التفاضلي</h3>
            <h3 class="lang-en">Level 1: D₀ – Differential derivative</h3>
            <p class="lang-ar">
              يمثل التغيّر اللحظي المعروف في التحليل الكلاسيكي، ويُعد قاعدة الهرم.
            </p>
            <p class="lang-en">
              Represents the classical instantaneous rate of change in standard analysis
              and forms the base of the hierarchy.
            </p>
          </div>

          <div class="card">
            <h3 class="lang-ar">المستوى الثاني: D₁ – المشتق النسبي</h3>
            <h3 class="lang-en">Level 2: D₁ – Relative derivative</h3>
            <p class="lang-ar">
              يعبّر عن التغيّر النسبي للتابع، ويرتبط بـ D₀ عبر العلاقة:
              <span dir="ltr">d₀ f = f · D₁ f</span>.
            </p>
            <p class="lang-en">
              Expresses the relative change of the function, tied to D₀ through
              <span dir="ltr">d₀ f = f · D₁ f</span>.
            </p>
          </div>

          <div class="card">
            <h3 class="lang-ar">المستويات الأعلى: D₂، D₃، وما بعدها</h3>
            <h3 class="lang-en">Higher levels: D₂, D₃, and beyond</h3>
            <p class="lang-ar">
              المشتق اللوغاريتمي D₂ والتتريشني D₃ يمهّدان لمستويات جديدة مرتبطة
              بالقوة المتكررة والتتريشن، مع إمكانية التعميم لمستويات بنتيشية،
              هيكساشنية، وهلم جرًّا.
            </p>
            <p class="lang-en">
              The logarithmic derivative D₂ and the tetrational derivative D₃ pave the
              way for new levels associated with repeated powers and tetration, with
              possible extensions to pentational, hexational, and higher stages.
            </p>
          </div>
        </div>
      </div>
    </section>

    <!-- Math structure -->
    <section id="math">
      <div class="container">
        <h2 class="section-title lang-ar">البنية الرياضية للمشتقات الهرمية</h2>
        <h2 class="section-title lang-en">Mathematical structure of the hierarchy</h2>

        <p class="section-subtitle lang-ar">
          هذا القسم يركّز على الصياغة الرياضية للعلاقات بين المشتقات، ويوضّح كيف
          يمكن أن يشكّل الحساب الهرمي نسقًا متماسكًا قابلاً للفحص والتطوير.
        </p>
        <p class="section-subtitle lang-en">
          This section emphasizes the mathematical formulation of the relations between
          derivative levels and shows how Hierarchical Calculus may form a coherent system
          suitable for examination and further development.
        </p>

        <div class="grid-2">
          <div class="card">
            <span class="pill lang-ar">التعريفات الأساسية</span>
            <span class="pill lang-en">Core definitions</span>

            <ul class="list">
              <li class="lang-ar">
                <strong>D₀ f(x)</strong>: المشتق التفاضلي التقليدي للتابع f.
              </li>
              <li class="lang-en">
                <strong>D₀ f(x)</strong>: the classical differential derivative of f.
              </li>

              <li class="lang-ar">
                <strong>D₁ f(x)</strong>: المشتق النسبي، بحيث
                <span dir="ltr">d₀ f = f · D₁ f</span>.
              </li>
              <li class="lang-en">
                <strong>D₁ f(x)</strong>: the relative derivative, with
                <span dir="ltr">d₀ f = f · D₁ f</span>.
              </li>

              <li class="lang-ar">
                <strong>D₂ f(x)</strong>: المشتق اللوغاريتمي، يحقّق
                <span dir="ltr">f(x)^{D₂ f(x)} = x^{D₁ f(x)}</span>.
              </li>
              <li class="lang-en">
                <strong>D₂ f(x)</strong>: the logarithmic derivative, satisfying
                <span dir="ltr">f(x)^{D₂ f(x)} = x^{D₁ f(x)}</span>.
              </li>

              <li class="lang-ar">
                <strong>D₃ f(x)</strong>: المشتق التتريشني، مع
                <span dir="ltr">f(x) ↑↑ D₃ f(x) = x ↑↑ D₂ f(x)</span>.
              </li>
              <li class="lang-en">
                <strong>D₃ f(x)</strong>: the tetrational derivative, with
                <span dir="ltr">f(x) ↑↑ D₃ f(x) = x ↑↑ D₂ f(x)</span>.
              </li>
            </ul>
          </div>

          <div class="card">
            <span class="pill lang-ar">أسئلة مفتوحة للبحث</span>
            <span class="pill lang-en">Open research questions</span>

            <ul class="list">
              <li class="lang-ar">
                كيف يمكن تدقيق مجالات التعريف لكل مستوى من المشتقات الهرمية؟
              </li>
              <li class="lang-en">
                How can the domains of definition be rigorously specified for each hierarchical derivative?
              </li>

              <li class="lang-ar">
                هل العلاقات الذهبية متّسقة في جميع الحالات، أم تظهر أمثلة مضادة؟
              </li>
              <li class="lang-en">
                Are the golden relations fully consistent, or do counterexamples arise?
              </li>

              <li class="lang-ar">
                ما علاقة هذه البنية بنظريات موجودة مثل الدوال الخاصة، التحليل المركب،
                أو الأنظمة الديناميكية؟
              </li>
              <li class="lang-en">
                How does this structure connect to existing theories such as special
                functions, complex analysis, or dynamical systems?
              </li>
            </ul>
          </div>
        </div>
      </div>
    </section>

    <!-- Cosmic hierarchy -->
    <section id="cosmos">
      <div class="container">
        <h2 class="section-title lang-ar">هرم الكون والحساب الهرمي</h2>
        <h2 class="section-title lang-en">Cosmic hierarchy and the calculus</h2>

        <p class="section-subtitle lang-ar">
          يمكن النظر إلى الحساب الهرمي على أنه ليس مجرد أداة رياضية، بل نموذج
          تصوّري لهرم الكون نفسه: من التغيّر الفيزيائي المباشر إلى العلاقات
          البنيوية والقوانين، ثم إلى مستويات أعلى تصف إنشاء الأكوان والقوانين ذاتها.
        </p>
        <p class="section-subtitle lang-en">
          Hierarchical Calculus can also be viewed as a conceptual model for the universe:
          from direct physical change to structural relations and laws, and further to
          meta-levels that may describe the generation of universes and laws themselves.
        </p>

        <div class="grid-3">
          <div class="card">
            <h3 class="lang-ar">الطبقة التفاضلية</h3>
            <h3 class="lang-en">Differential layer</h3>
            <p class="lang-ar">
              تمثّل الحركة المباشرة، الطاقة، والزمن – أي التغيّرات الفيزيائية
              اللحظية التي يقابلها D₀.
            </p>
            <p class="lang-en">
              Represents motion, energy, and time: the immediate physical changes
              modeled by D₀.
            </p>
          </div>

          <div class="card">
            <h3 class="lang-ar">الطبقة النسبية واللوغاريتمية</h3>
            <h3 class="lang-en">Relative and logarithmic layers</h3>
            <p class="lang-ar">
              تصف نسب العلاقات بين الكتل والثوابت والبنى، ثم تضغط هذه العلاقات
              في صيغ لوغاريتمية أكثر تجريدًا (D₁ و D₂).
            </p>
            <p class="lang-en">
              Describe relative ratios between masses, constants, and structures, then
              compress these patterns into more abstract logarithmic forms (D₁ and D₂).
            </p>
          </div>

          <div class="card">
            <h3 class="lang-ar">الطبقات التتريشنية وما فوقها</h3>
            <h3 class="lang-en">Tetrational and higher layers</h3>
            <p class="lang-ar">
              تمثّل مستويات "فوق القوانين"، حيث تُبنى الأكوان أو القوانين نفسها
              كجزء من هرم عمليات أعمق (D₃ وما بعده).
            </p>
            <p class="lang-en">
              Represent “beyond-the-laws” levels, where universes or laws themselves are
              generated as part of a deeper operational hierarchy (D₃ and beyond).
            </p>
          </div>
        </div>
      </div>
    </section>

    <!-- Why new + library -->
    <section id="new">
      <div class="container">
        <h2 class="section-title lang-ar">لماذا يُعد هذا العلم جديدًا؟</h2>
        <h2 class="section-title lang-en">Why is this theory considered new?</h2>

        <p class="section-subtitle lang-ar">
          بقدر ما يعلم المؤلف، لا يوجد في المناهج أو المراجع الرياضية الحالية فرع
          مستقل يُدعى "الحساب الهرمي" بهذه الصياغة. إنّه طرح شخصي يُعرض بوضوح كمادة
          بحثية مفتوحة للنقد والتطوير.
        </p>
        <p class="section-subtitle lang-en">
          As far as the author is aware, there is no established branch in current
          mathematical curricula called “Hierarchical Calculus” in this form. It is a
          personal proposal, explicitly presented as open research material for critique
          and development.
        </p>

        <div class="grid-3">
          <div class="card">
            <h3 class="lang-ar">خارج المنظومة التقليدية</h3>
            <h3 class="lang-en">Outside traditional frameworks</h3>
            <p class="lang-ar">
              لا يُدرَّس الحساب الهرمي في المدارس أو الجامعات. إنه مبادرة فردية
              تُطرح أمام المجتمع العلمي لاختبارها.
            </p>
            <p class="lang-en">
              Hierarchical Calculus is not part of school or university programs. It is
              a personal initiative brought before the scientific community for testing.
            </p>
          </div>

          <div class="card">
            <h3 class="lang-ar">تنظيم هرمي للمشتقات</h3>
            <h3 class="lang-en">Hierarchical organization of derivatives</h3>
            <p class="lang-ar">
              تحاول النظرية ربط أنواع مختلفة من المشتقات ضمن هرم واحد بدل التعامل
              معها كأدوات منفصلة.
            </p>
            <p class="lang-en">
              The theory attempts to connect different derivative notions inside a single
              hierarchy instead of treating them as isolated tools.
            </p>
          </div>

          <div class="card">
            <h3 class="lang-ar">دعوة مفتوحة للعلماء</h3>
            <h3 class="lang-en">Open invitation to scientists</h3>
            <p class="lang-ar">
              صُمّم هذا الموقع بالأساس لعرض الفكرة على المتخصصين، لا لادّعاء
              اكتمالها، بل لدعوتهم إلى مراجعتها وتطويرها أو حتى معارضتها علميًا.
            </p>
            <p class="lang-en">
              This site is designed primarily to present the idea to specialists, not to
              claim its completeness, but to invite them to refine, extend, or even
              scientifically oppose it.
            </p>
          </div>
        </div>
      </div>
    </section>

    <!-- Library -->
    <section id="library">
      <div class="container">
        <h2 class="section-title lang-ar">مكتبة الحساب الهرمي</h2>
        <h2 class="section-title lang-en">Hierarchical Calculus Library</h2>

        <p class="section-subtitle lang-ar">
          يملك المؤلف موقعًا ومواد مكتوبة تمتد عبر ٣٢ فصلًا، يمكن ربطها لاحقًا
          هنا كمرجع تفصيلي للنظرية، من التعريفات الأولى حتى التطبيقات الكونية.
        </p>
        <p class="section-subtitle lang-en">
          The author has a written corpus spanning 32 chapters, which can later be linked
          here as a detailed reference to the theory: from basic definitions to cosmic
          interpretations.
        </p>

        <div class="card">
          <p class="lang-ar">
            في النسخة الحالية، تم تخصيص هذا القسم كمكان منظم لإضافة روابط الفصول
            والملفات (PDF أو صفحات ويب). يمكنك مستقبلاً إدراج:
          </p>
          <p class="lang-en">
            In this initial version, this section is reserved as a structured place to
            add links to chapters and files (PDFs or web pages). In the future, you may
            include:
          </p>

          <ul class="list">
            <li class="lang-ar">روابط للفصول الـ ٣٢ مرتّبة حسب الموضوع والمستوى.</li>
            <li class="lang-en">Links to the 32 chapters, organized by topic and level.</li>

            <li class="lang-ar">نسخ قابلة للتحميل للأبحاث أو المسودات.</li>
            <li class="lang-en">Downloadable versions of drafts or research notes.</li>

            <li class="lang-ar">ملفات تمارين وأمثلة تطبيقية على المشتقات الهرمية.</li>
            <li class="lang-en">Exercises and applied examples using hierarchical derivatives.</li>
          </ul>

          <div class="chapters-box">
            <span class="chap-pill lang-ar">الفصل 1</span>
            <span class="chap-pill lang-ar">الفصل 2</span>
            <span class="chap-pill lang-ar">الفصل 3</span>
            <span class="chap-pill lang-ar">... حتى الفصل 32</span>

            <span class="chap-pill lang-en">Chapter 1</span>
            <span class="chap-pill lang-en">Chapter 2</span>
            <span class="chap-pill lang-en">Chapter 3</span>
            <span class="chap-pill lang-en">… up to Chapter 32</span>
          </div>
        </div>
      </div>
    </section>

    <!-- Author & contact -->
    <section id="contact">
      <div class="container">
        <h2 class="section-title lang-ar">عن المؤلف والتواصل</h2>
        <h2 class="section-title lang-en">About the author & contact</h2>

        <div class="grid-2">
          <div class="card">
            <h3 class="lang-ar">المؤلف</h3>
            <h3 class="lang-en">The author</h3>

            <p class="lang-ar">
              الحساب الهرمي هو طرح من إعداد <strong>أحمد أحمد</strong>، يُقدَّم
              هنا كفكرة رياضية وفلسفية حول المشتقات وهرمية العمليات، مع رؤية
              كونية مرافقة. الهدف هو فتح باب النقاش مع العلماء لا تقديم حقيقة
              نهائية.
            </p>
            <p class="lang-en">
              Hierarchical Calculus is proposed by <strong>Ahmed Ahmed</strong> as a
              mathematical and philosophical idea about derivatives and operational
              hierarchies, accompanied by a cosmic vision. The goal is to open a
              discussion with scientists, not to present a final truth.
            </p>
          </div>

          <div class="contact-box">
            <p class="lang-ar">
              للبريد العلمي، الملاحظات، أو اقتراح التعاون:
            </p>
            <p class="lang-en">
              For scientific feedback, comments, or collaboration proposals:
            </p>

            <p>
              📧
              <a href="mailto:ahmedgossa50@gmail.com">
                ahmedgossa50@gmail.com
              </a>
            </p>

            <p class="lang-ar">
              يمكنك إرسال نقد رياضي، أمثلة مضادة، أو اقتراحات لتحسين الصياغة
              الحالية للحساب الهرمي.
            </p>
            <p class="lang-en">
              You are invited to send mathematical critiques, counterexamples, or
              suggestions to improve the current formulation of Hierarchical Calculus.
            </p>
          </div>
        </div>
      </div>
    </section>
  </main>

  <footer>
    © <span id="year"></span>
    <span class="lang-ar">الحساب الهرمي – طرح رياضي شخصي قيد التطوير.</span>
    <span class="lang-en">Hierarchical Calculus – personal mathematical proposal in progress.</span>
  </footer>

  <script>
    // تحديث السنة في الفوتر
    document.getElementById("year").textContent = new Date().getFullYear();

    // تبديل اللغة
    const toggleBtn = document.getElementById("langToggle");
    function setLang(lang) {
      if (lang === "en") {
        document.body.classList.add("show-en");
        document.documentElement.lang = "en";
        document.documentElement.dir = "ltr";
        toggleBtn.querySelector("span").textContent = "EN";
        localStorage.setItem("hc_lang", "en");
      } else {
        document.body.classList.remove("show-en");
        document.documentElement.lang = "ar";
        document.documentElement.dir = "rtl";
        toggleBtn.querySelector("span").textContent = "AR";
        localStorage.setItem("hc_lang", "ar");
      }
    }

    // تحميل اللغة المخزنة إن وُجدت
    const savedLang = localStorage.getItem("hc_lang") || "ar";
    setLang(savedLang);

    toggleBtn.addEventListener("click", () => {
      const current = document.body.classList.contains("show-en") ? "en" : "ar";
      setLang(current === "ar" ? "en" : "ar");
    });
  </script>
</body>
</html>
