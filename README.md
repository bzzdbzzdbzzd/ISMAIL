import React, { useMemo, useState } from "react";
import {
  Phone,
  Mail,
  ArrowRight,
  Globe2,
  ShieldCheck,
  PackageCheck,
  Truck,
  Factory,
  MapPin,
  Send,
  Leaf,
  Cherry,
} from "lucide-react";
import { Button } from "@/components/ui/button";

const CONTACT = {
  brand: "ISMAIL",
  phoneDisplay: "+996 500 118 703",
  phoneLink: "+996500118703",
  email: "ismail.yagoda@yandex.kg",
  location: {
    en: "Bishkek, Kyrgyzstan",
    ru: "Бишкек, Кыргызстан",
  },
};

const content = {
  en: {
    nav: {
      brandSubtitle: "Frozen berries · Kyrgyzstan",
      exportCardTitle: "Frozen Berry Export",
      products: "Products",
      quality: "Quality",
      markets: "Markets",
      about: "About",
      contact: "Contact",
      quote: "Request quote",
    },
    hero: {
      label: "Wholesale frozen berries · Kyrgyzstan",
      title: "Natural frozen berries for global supply.",
      text: "ISMAIL supplies selected frozen berries for importers, distributors, food manufacturers, cafés, bakeries and private wholesale buyers.",
      primary: "Request export price",
      secondary: "View products",
    },
    stats: [
      { value: "20+", label: "Years in the market" },
      { value: "100K+", label: "Completed deals" },
      { value: "≈2M", label: "Tons exported" },
    ],
    products: {
      label: "Product range",
      title: "Frozen berries for wholesale orders.",
      text: "Choose one berry type or request a mixed order. Packaging, volume and delivery terms are discussed individually.",
      note: "Wholesale · cold chain · export-ready",
    },
    productList: [
      { name: "Frozen Raspberry", detail: "Aromatic berry for desserts, jams, smoothies and production." },
      { name: "Frozen Strawberry", detail: "Popular sweet berry for cafés, bakeries, retail and processing." },
      { name: "Frozen Blackcurrant", detail: "Rich taste for juices, sauces, fillings and healthy products." },
      { name: "Frozen Sea Buckthorn", detail: "Bright sour berry for teas, drinks, concentrates and wellness products." },
    ],
    quality: {
      label: "Quality & logistics",
      title: "Quality, cold chain and clear communication.",
      text: "International buyers need predictable supply, clean sorting, proper packing and fast communication at every order stage.",
      items: [
        { title: "Selection & sorting", text: "Berries are selected and sorted before packing for consistent quality." },
        { title: "Shock freezing", text: "Products are frozen quickly and prepared for cold-chain delivery." },
        { title: "Wholesale packing", text: "Bulk packaging options are available for distributors and manufacturers." },
        { title: "Export support", text: "Order details, documents and delivery requirements can be discussed before shipment." },
      ],
    },
    markets: {
      label: "Who we serve",
      title: "For buyers who need reliable volume.",
      text: "ISMAIL works with different buyer types — from large companies to private wholesale customers.",
      list: ["Importers", "Distributors", "Food manufacturers", "Cafés & bakeries", "Retail brands", "Private wholesale buyers"],
    },
    about: {
      label: "About us",
      title: "A berry supplier with long-term market experience.",
      text: "For over 20 years, ISMAIL has been operating in the frozen berry market. During this time, we have successfully completed more than 100,000 deals and exported around 2 million tons of berries to large companies and private customers.",
    },
    contact: {
      label: "Contact",
      title: "Request a wholesale quote.",
      text: "Send your product type, quantity, packaging request and destination. We will prepare a clear offer for your order.",
      name: "Name / Company",
      contact: "Email or phone",
      product: "Product",
      select: "Select product",
      mixed: "Mixed order",
      message: "Quantity, destination, packaging, deadline...",
      send: "Send request by email",
      subject: "Frozen berries order request",
      mailName: "Name",
      mailContact: "Contact",
      mailProduct: "Product",
      mailMessage: "Message",
      response: "Fast response for wholesale and export inquiries",
    },
    footer: {
      line: "Frozen berries from Kyrgyzstan for wholesale and export.",
    },
  },
  ru: {
    nav: {
      brandSubtitle: "Замороженные ягоды · Кыргызстан",
      exportCardTitle: "Экспорт ягод из Кыргызстана",
      products: "Продукция",
      quality: "Качество",
      markets: "Покупатели",
      about: "О нас",
      contact: "Контакты",
      quote: "Запросить цену",
    },
    hero: {
      label: "Оптовые замороженные ягоды · Кыргызстан",
      title: "Натуральные ягоды шоковой заморозки для мирового рынка.",
      text: "ISMAIL поставляет отборные замороженные ягоды для импортеров, дистрибьюторов, пищевых производств, кафе, пекарен и частных оптовых покупателей.",
      primary: "Запросить экспортную цену",
      secondary: "Смотреть продукцию",
    },
    stats: [
      { value: "20+", label: "Лет на рынке" },
      { value: "100K+", label: "Успешных сделок" },
      { value: "≈2M", label: "Тонн экспортировано" },
    ],
    products: {
      label: "Ассортимент",
      title: "Замороженные ягоды для оптовых заказов.",
      text: "Выберите один вид ягоды или запросите смешанный заказ. Упаковка, объем и условия доставки обсуждаются индивидуально.",
      note: "Опт · холодная цепь · экспорт",
    },
    productList: [
      { name: "Замороженная малина", detail: "Ароматная ягода для десертов, джемов, смузи и производства." },
      { name: "Замороженная клубника", detail: "Популярная сладкая ягода для кафе, пекарен, розницы и переработки." },
      { name: "Замороженная черная смородина", detail: "Насыщенный вкус для соков, соусов, начинок и полезных продуктов." },
      { name: "Замороженная облепиха", detail: "Яркая кислая ягода для чая, напитков, концентратов и wellness-продуктов." },
    ],
    quality: {
      label: "Качество и логистика",
      title: "Качество, холодная цепь и понятная коммуникация.",
      text: "Международным покупателям важны стабильные поставки, чистая сортировка, аккуратная упаковка и быстрая связь на каждом этапе заказа.",
      items: [
        { title: "Отбор и сортировка", text: "Ягоды проходят отбор и сортировку перед упаковкой для стабильного качества." },
        { title: "Шоковая заморозка", text: "Продукция быстро замораживается и готовится к доставке по холодной цепи." },
        { title: "Оптовая упаковка", text: "Доступны крупные упаковки для дистрибьюторов и производственных покупателей." },
        { title: "Экспортное сопровождение", text: "Детали заказа, документы и условия доставки можно обсудить перед отправкой." },
      ],
    },
    markets: {
      label: "Для кого мы работаем",
      title: "Для покупателей, которым нужен надежный объем.",
      text: "ISMAIL работает с разными категориями покупателей — от крупных компаний до частных оптовых клиентов.",
      list: ["Импортеры", "Дистрибьюторы", "Пищевые производства", "Кафе и пекарни", "Розничные бренды", "Частные оптовые покупатели"],
    },
    about: {
      label: "О нас",
      title: "Поставщик ягод с большим опытом на рынке.",
      text: "Компания ISMAIL работает на рынке замороженных ягод уже более 20 лет. За это время мы успешно совершили свыше 100 000 сделок и экспортировали около 2 миллионов тонн ягод крупным компаниям и частным клиентам.",
    },
    contact: {
      label: "Контакты",
      title: "Запросите оптовое предложение.",
      text: "Отправьте вид продукции, объем, упаковку и направление доставки. Мы подготовим понятное предложение под ваш заказ.",
      name: "Имя / Компания",
      contact: "Email или телефон",
      product: "Продукт",
      select: "Выберите продукт",
      mixed: "Смешанный заказ",
      message: "Количество, направление, упаковка, сроки...",
      send: "Отправить заявку на почту",
      subject: "Запрос на замороженные ягоды",
      mailName: "Имя",
      mailContact: "Контакт",
      mailProduct: "Продукт",
      mailMessage: "Сообщение",
      response: "Быстрый ответ по оптовым и экспортным заявкам",
    },
    footer: {
      line: "Замороженные ягоды из Кыргызстана для опта и экспорта.",
    },
  },
};

const qualityIcons = [ShieldCheck, Cherry, PackageCheck, Truck];
const marketIcons = [Globe2, Truck, Factory, PackageCheck, ShieldCheck, MapPin];
const productAccents = ["#b52f33", "#d44a4f", "#4f7b43", "#8a5a16"];

function runSmokeTests() {
  ["en", "ru"].forEach((language) => {
    const block = content[language];
    console.assert(block.productList.length === 4, `${language}: product list should contain 4 items`);
    console.assert(block.stats.length === 3, `${language}: stats should contain 3 items`);
    console.assert(block.quality.items.length === qualityIcons.length, `${language}: quality icons should match quality items`);
    console.assert(block.markets.list.length === marketIcons.length, `${language}: market icons should match market items`);
    console.assert(Boolean(block.nav.exportCardTitle), `${language}: export card title should exist`);
    console.assert(!String(qualityIcons).includes("Snowflake"), "Snowflake must not be referenced anywhere");
    console.assert(typeof StrawberryAvatar === "function", "StrawberryAvatar component should exist");
    console.assert(typeof ProductVisual === "function", "ProductVisual component should exist");
  });
}

if (typeof console !== "undefined") {
  runSmokeTests();
}

function StrawberryAvatar() {
  return (
    <svg
      viewBox="0 0 100 100"
      className="h-full w-full"
      aria-label="Strawberry avatar"
      role="img"
    >
      <defs>
        <linearGradient id="strawberryBg" x1="0" y1="0" x2="1" y2="1">
          <stop offset="0%" stopColor="#f7fff2" />
          <stop offset="100%" stopColor="#edf8e8" />
        </linearGradient>
        <linearGradient id="strawberryBody" x1="0" y1="0" x2="0" y2="1">
          <stop offset="0%" stopColor="#ff5a5f" />
          <stop offset="100%" stopColor="#c91822" />
        </linearGradient>
        <linearGradient id="strawberryLeaf" x1="0" y1="0" x2="1" y2="1">
          <stop offset="0%" stopColor="#76d65a" />
          <stop offset="100%" stopColor="#2f8e35" />
        </linearGradient>
      </defs>

      <circle cx="50" cy="50" r="50" fill="url(#strawberryBg)" />
      <circle cx="50" cy="50" r="47" fill="none" stroke="#d7e8cf" strokeWidth="2" />
      <ellipse cx="32" cy="22" rx="12" ry="7" transform="rotate(-28 32 22)" fill="url(#strawberryLeaf)" />
      <ellipse cx="50" cy="18" rx="12" ry="8" fill="url(#strawberryLeaf)" />
      <ellipse cx="68" cy="22" rx="12" ry="7" transform="rotate(28 68 22)" fill="url(#strawberryLeaf)" />
      <path d="M50 23 L58 34 L42 34 Z" fill="#4fa83f" />
      <path
        d="M50 28 C67 28 77 42 75 58 C73 76 60 88 50 92 C40 88 27 76 25 58 C23 42 33 28 50 28 Z"
        fill="url(#strawberryBody)"
        stroke="#b1121b"
        strokeWidth="2"
      />
      <ellipse cx="39" cy="40" rx="10" ry="18" fill="rgba(255,255,255,0.16)" transform="rotate(18 39 40)" />
      {[
        [41, 42, -15], [50, 40, 0], [59, 42, 15], [37, 52, -20], [46, 51, -8], [54, 51, 8],
        [63, 52, 20], [41, 62, -15], [50, 61, 0], [59, 62, 15], [46, 72, -8], [54, 72, 8],
      ].map(([cx, cy, rotation], index) => (
        <ellipse key={index} cx={cx} cy={cy} rx="2" ry="3.5" fill="#ffd966" transform={`rotate(${rotation} ${cx} ${cy})`} />
      ))}
    </svg>
  );
}

function ProductVisual({ index, name }) {
  const visuals = [
    { bg: "from-[#fff1f2] via-white to-[#eef8e8]", berry: "#d71920", berry2: "#f24a50", leaf: "#4f7b43", label: "RASPBERRY" },
    { bg: "from-[#fff2ef] via-white to-[#edf8e8]", berry: "#e22a2f", berry2: "#ff6368", leaf: "#3f8a36", label: "STRAWBERRY" },
    { bg: "from-[#f2eefb] via-white to-[#eef8e8]", berry: "#34204f", berry2: "#5b3b83", leaf: "#4f7b43", label: "CURRANT" },
    { bg: "from-[#fff4dd] via-white to-[#eef8e8]", berry: "#f08a22", berry2: "#ffb347", leaf: "#5f8f4d", label: "SEA BUCKTHORN" },
  ];

  const visual = visuals[index % visuals.length];

  return (
    <div className={`relative mb-6 h-44 overflow-hidden rounded-[1.35rem] bg-gradient-to-br ${visual.bg} shadow-inner`}>
      <div className="absolute -right-8 -top-8 h-28 w-28 rounded-full bg-white/70" />
      <div className="absolute -bottom-10 -left-8 h-28 w-28 rounded-full bg-green-100/70" />
      <div className="absolute left-5 top-5 rounded-full bg-white/80 px-3 py-1 text-[10px] font-bold uppercase tracking-[0.18em] text-[#5b524a] shadow-sm">
        {visual.label}
      </div>

      <svg viewBox="0 0 240 150" className="absolute inset-0 h-full w-full" aria-label={name} role="img">
        <defs>
          <linearGradient id={`productBerry-${index}`} x1="0" y1="0" x2="0" y2="1">
            <stop offset="0%" stopColor={visual.berry2} />
            <stop offset="100%" stopColor={visual.berry} />
          </linearGradient>
          <filter id={`productShadow-${index}`} x="-20%" y="-20%" width="140%" height="140%">
            <feDropShadow dx="0" dy="9" stdDeviation="7" floodColor="#6b1d1d" floodOpacity="0.18" />
          </filter>
        </defs>

        <path d="M55 97 C75 65, 105 50, 137 57 C166 63, 188 84, 195 112" fill="none" stroke={visual.leaf} strokeWidth="7" strokeLinecap="round" opacity="0.85" />
        <ellipse cx="80" cy="68" rx="22" ry="10" fill={visual.leaf} transform="rotate(-28 80 68)" opacity="0.9" />
        <ellipse cx="158" cy="70" rx="22" ry="10" fill={visual.leaf} transform="rotate(25 158 70)" opacity="0.9" />

        {index === 1 ? (
          <g filter={`url(#productShadow-${index})`}>
            <path d="M120 38 C151 38 170 62 167 91 C164 118 137 133 120 139 C103 133 76 118 73 91 C70 62 89 38 120 38Z" fill={`url(#productBerry-${index})`} />
            <path d="M92 38 C102 30 113 32 120 43 C127 32 138 30 148 38 C138 41 129 44 120 51 C111 44 102 41 92 38Z" fill={visual.leaf} />
            {[104, 120, 136, 96, 114, 132, 106, 124, 142].map((x, i) => (
              <ellipse key={i} cx={x} cy={62 + (i % 3) * 22} rx="2.5" ry="4" fill="#ffd867" transform={`rotate(${i % 2 ? -12 : 14} ${x} ${62 + (i % 3) * 22})`} />
            ))}
          </g>
        ) : (
          <g filter={`url(#productShadow-${index})`}>
            {[70, 96, 122, 148, 174, 84, 110, 136, 162, 98, 124, 150].map((x, i) => (
              <circle
                key={i}
                cx={x}
                cy={64 + Math.floor(i / 5) * 25 + (i % 2) * 5}
                r={index === 3 ? 12 : 15}
                fill={`url(#productBerry-${index})`}
              />
            ))}
            <circle cx="95" cy="60" r="4" fill="rgba(255,255,255,0.45)" />
            <circle cx="145" cy="78" r="4" fill="rgba(255,255,255,0.35)" />
          </g>
        )}
      </svg>
    </div>
  );
}

export default function IsmailFrozenBerriesWebsite() {
  const [lang, setLang] = useState("en");
  const [form, setForm] = useState({
    name: "",
    contact: "",
    product: "",
    message: "",
  });

  const t = content[lang];
  const productNames = useMemo(() => t.productList.map((item) => item.name), [t.productList]);

  const mailSubject = encodeURIComponent(t.contact.subject);
  const mailBody = encodeURIComponent(
    `${t.contact.mailName}: ${form.name}\n${t.contact.mailContact}: ${form.contact}\n${t.contact.mailProduct}: ${form.product}\n${t.contact.mailMessage}: ${form.message}`
  );

  const handleProductClick = (productName) => {
    setForm((current) => ({ ...current, product: productName }));
  };

  return (
    <main className="min-h-screen overflow-x-hidden bg-[#fffaf6] text-[#2d261f] antialiased">
      <style>{`
        @import url('https://fonts.googleapis.com/css2?family=Inter:wght@400;500;600;700;800&family=Space+Grotesk:wght@500;600;700&display=swap');

        html { scroll-behavior: smooth; }

        body {
          font-family: 'Inter', sans-serif;
          -webkit-font-smoothing: antialiased;
          -moz-osx-font-smoothing: grayscale;
          background: #fffaf6;
        }

        .font-display { font-family: 'Space Grotesk', sans-serif; }
        .text-balance { text-wrap: balance; }
        .text-pretty { text-wrap: pretty; }

        .berry-text {
          background: linear-gradient(90deg, #b52f33 0%, #9b7a2e 42%, #4f7b43 100%);
          -webkit-background-clip: text;
          background-clip: text;
          color: transparent;
        }

        .berry-border-soft {
          border: 1px solid transparent;
          background:
            linear-gradient(#ffffff, #ffffff) padding-box,
            linear-gradient(135deg, #efb7bb 0%, #dbc27b 42%, #b8d5a8 100%) border-box;
        }

        .berry-border-cream {
          border: 1px solid transparent;
          background:
            linear-gradient(#fffaf7, #fffaf7) padding-box,
            linear-gradient(135deg, #efb7bb 0%, #dbc27b 42%, #b8d5a8 100%) border-box;
        }

        .berry-border-dark {
          border: 1px solid transparent;
          background:
            linear-gradient(135deg, rgba(255,255,255,0.10), rgba(255,255,255,0.10)) padding-box,
            linear-gradient(135deg, rgba(255,120,120,0.45), rgba(226,191,92,0.40), rgba(131,192,121,0.45)) border-box;
        }

        .berry-button { background: linear-gradient(135deg, #b52f33 0%, #9b7a2e 48%, #4f7b43 100%); }
        .berry-button:hover { background: linear-gradient(135deg, #9d262c 0%, #8a6d27 48%, #416b38 100%); }

        .export-card-shell {
          border: 2px solid transparent;
          background:
            linear-gradient(#ffffff, #ffffff) padding-box,
            linear-gradient(135deg, #3f6f36 0%, #8db96f 28%, #b52f33 62%, #4f7b43 100%) border-box;
          box-shadow:
            0 28px 90px rgba(79, 123, 67, 0.32),
            0 0 0 10px rgba(111, 158, 86, 0.12),
            inset 0 0 0 1px rgba(255, 255, 255, 0.7);
        }

        .export-inner-glow {
          box-shadow:
            inset 0 1px 0 rgba(255, 255, 255, 0.18),
            inset 0 -36px 80px rgba(24, 55, 24, 0.18),
            0 18px 40px rgba(37, 78, 36, 0.24);
        }

        .export-title-shadow {
          text-shadow: 0 3px 14px rgba(0,0,0,0.32), 0 1px 2px rgba(0,0,0,0.22);
        }

        .export-number-shadow {
          text-shadow: 0 4px 16px rgba(0,0,0,0.34), 0 1px 2px rgba(0,0,0,0.22);
        }

        .export-label-shadow { text-shadow: 0 1px 4px rgba(0,0,0,0.26); }

        .export-stat-card {
          background: rgba(255, 255, 255, 0.18);
          border: 1px solid rgba(255, 255, 255, 0.26);
          box-shadow: inset 0 1px 0 rgba(255,255,255,0.16), 0 10px 24px rgba(28,63,28,0.16);
          backdrop-filter: blur(8px);
        }
      `}</style>

      <header className="sticky top-0 z-50 border-b border-[#d9e5d0] bg-[#fffaf6]/92 backdrop-blur-xl">
        <div className="mx-auto flex max-w-7xl items-center justify-between gap-4 px-5 py-4">
          <a href="#home" className="flex min-w-0 items-center gap-3" aria-label="ISMAIL home">
            <div className="h-12 w-12 shrink-0 overflow-hidden rounded-full berry-border-soft bg-white p-0.5 shadow-sm">
              <StrawberryAvatar />
            </div>
            <div className="min-w-0 leading-tight">
              <p className="font-display text-2xl font-bold uppercase tracking-[0.18em] berry-text">{CONTACT.brand}</p>
              <p className="hidden truncate text-[11px] font-medium uppercase tracking-[0.22em] text-[#6e675f] sm:block">
                {t.nav.brandSubtitle}
              </p>
            </div>
          </a>

          <nav className="hidden items-center gap-6 text-[12px] font-semibold uppercase tracking-[0.13em] text-[#665d55] xl:flex">
            <a href="#products" className="transition hover:text-[#5e7f47]">{t.nav.products}</a>
            <a href="#quality" className="transition hover:text-[#5e7f47]">{t.nav.quality}</a>
            <a href="#markets" className="transition hover:text-[#5e7f47]">{t.nav.markets}</a>
            <a href="#about" className="transition hover:text-[#5e7f47]">{t.nav.about}</a>
            <a href="#contact" className="transition hover:text-[#5e7f47]">{t.nav.contact}</a>
          </nav>

          <div className="flex shrink-0 items-center gap-3">
            <a href="#contact" className="hidden lg:block">
              <Button className="rounded-full berry-button px-5 py-5 text-[11px] font-semibold uppercase tracking-[0.14em] text-white">
                {t.nav.quote}
              </Button>
            </a>
            <div className="flex rounded-full berry-border-soft bg-white p-1 text-sm shadow-sm">
              <button
                type="button"
                onClick={() => setLang("en")}
                className={`rounded-full px-3 py-1.5 text-[12px] font-semibold transition ${lang === "en" ? "berry-button text-white" : "text-[#665d55] hover:text-[#5e7f47]"}`}
              >
                EN
              </button>
              <button
                type="button"
                onClick={() => setLang("ru")}
                className={`rounded-full px-3 py-1.5 text-[12px] font-semibold transition ${lang === "ru" ? "berry-button text-white" : "text-[#665d55] hover:text-[#5e7f47]"}`}
              >
                RU
              </button>
            </div>
          </div>
        </div>
      </header>

      <section id="home" className="relative mx-auto grid max-w-7xl gap-12 overflow-hidden px-5 py-16 md:grid-cols-[1.05fr_0.95fr] md:items-center md:py-24">
        <div className="pointer-events-none absolute -left-16 top-10 h-56 w-56 rounded-full bg-red-200/40 blur-3xl" />
        <div className="pointer-events-none absolute right-10 top-16 h-52 w-52 rounded-full bg-green-200/40 blur-3xl" />
        <div className="pointer-events-none absolute bottom-0 left-1/3 h-40 w-40 rounded-full bg-red-100/50 blur-3xl" />

        <div className="relative min-w-0">
          <div className="mb-6 inline-flex max-w-full items-center gap-2 rounded-full berry-border-soft bg-white px-4 py-2 text-[11px] font-semibold uppercase tracking-[0.16em] text-[#6a6158] shadow-sm sm:text-[12px]">
            <Leaf className="h-4 w-4 shrink-0 text-[#5c8b45]" />
            <span className="truncate">{t.hero.label}</span>
          </div>

          <h1 className={`font-display text-balance max-w-4xl font-bold leading-[0.94] tracking-[-0.05em] berry-text ${lang === "ru" ? "text-[38px] sm:text-[46px] md:text-[58px] lg:text-[68px]" : "text-5xl uppercase sm:text-6xl md:text-7xl lg:text-[80px]"}`}>
            {t.hero.title}
          </h1>

          <p className="text-pretty mt-7 max-w-2xl text-[17px] leading-8 text-[#5f564e] md:text-[19px] md:leading-9">{t.hero.text}</p>

          <div className="mt-9 flex flex-col gap-3 sm:flex-row">
            <a href="#contact" className="w-full sm:w-auto">
              <Button className="w-full rounded-full berry-button px-8 py-6 text-[12px] font-semibold uppercase tracking-[0.13em] text-white sm:w-auto sm:text-[13px]">
                {t.hero.primary} <ArrowRight className="ml-2 h-4 w-4" />
              </Button>
            </a>
            <a href="#products" className="w-full sm:w-auto">
              <Button
                variant="outline"
                className={`w-full min-w-[220px] whitespace-nowrap rounded-full border-transparent bg-gradient-to-r from-[#fff2ef] via-[#f5ead2] to-[#eef6ea] px-8 py-6 font-semibold uppercase text-[#4a6c3d] hover:bg-[#e3f0dc] sm:w-auto ${lang === "ru" ? "text-[11px] tracking-[0.08em] sm:text-[12px]" : "text-[12px] tracking-[0.13em] sm:text-[13px]"}`}
              >
                {t.hero.secondary}
              </Button>
            </a>
          </div>
        </div>

        <div className="relative min-w-0">
          <div className="pointer-events-none absolute -inset-4 rounded-[2.5rem] bg-gradient-to-br from-red-100 via-white to-green-100 blur-2xl" />
          <div className="export-card-shell relative overflow-hidden rounded-[2rem] bg-white p-4 sm:p-5">
            <div className="export-inner-glow relative overflow-hidden rounded-[1.5rem] bg-gradient-to-br from-[#244f24] via-[#4f7b43] to-[#9bc476] p-6 text-white">
              <div className="pointer-events-none absolute -right-10 -top-10 h-32 w-32 rounded-full bg-white/12 blur-sm" />
              <div className="pointer-events-none absolute top-20 right-16 h-16 w-28 rotate-[35deg] rounded-full bg-white/10 blur-sm" />
              <div className="pointer-events-none absolute bottom-14 left-10 h-14 w-24 -rotate-[28deg] rounded-full bg-white/10 blur-sm" />
              <div className="pointer-events-none absolute -bottom-10 left-1/4 h-24 w-24 rounded-full bg-[#d9f0d0]/20 blur-xl" />

              <div className="relative flex items-start justify-between gap-4">
                <div className="min-w-0">
                  <p className="export-label-shadow text-sm font-semibold uppercase tracking-[0.14em] text-white/90">{CONTACT.brand}</p>
                  <h2 className={`export-title-shadow font-display mt-2 text-balance font-bold leading-[1.02] tracking-[-0.04em] text-white ${lang === "ru" ? "text-[31px] sm:text-[34px]" : "text-[32px] uppercase sm:text-[36px]"}`}>
                    {t.nav.exportCardTitle}
                  </h2>
                </div>
                <div className="flex h-11 w-11 shrink-0 items-center justify-center rounded-full bg-white/12 backdrop-blur-sm">
                  <Leaf className="h-5 w-5 text-white/90" />
                </div>
              </div>

              <div className="relative mt-8 grid gap-3">
                {t.stats.map((stat) => (
                  <div key={stat.label} className="export-stat-card rounded-2xl p-5">
                    <p className="export-number-shadow font-display text-[52px] font-extrabold uppercase leading-none tracking-[-0.06em] text-white sm:text-[58px]">{stat.value}</p>
                    <p className="export-label-shadow mt-3 text-[12px] font-semibold uppercase tracking-[0.16em] text-white/95">{stat.label}</p>
                  </div>
                ))}
              </div>

              <div className="relative mt-6 rounded-2xl bg-white p-5 text-[#2d261f]">
                <p className="text-pretty text-[14px] font-medium leading-6 text-[#4f463f]">{t.contact.response}</p>
                <div className="mt-4 flex flex-wrap items-center gap-3">
                  <a href={`tel:${CONTACT.phoneLink}`} className="font-semibold text-[17px] text-[#35662f] hover:underline">{CONTACT.phoneDisplay}</a>
                </div>
              </div>
            </div>
          </div>
        </div>
      </section>

      <section className="border-y border-[#d9e5d0] bg-white">
        <div className="mx-auto grid max-w-7xl gap-4 px-5 py-6 md:grid-cols-3">
          {t.stats.map((stat, index) => (
            <div key={stat.label} className={`flex min-h-32 items-end justify-between gap-4 overflow-hidden rounded-3xl p-6 ${index === 1 ? "bg-[#eef6ea]" : "bg-[#fff4f1]"}`}>
              <p className={`font-display shrink-0 text-5xl font-bold uppercase tracking-[-0.05em] ${index === 1 ? "text-[#4f7b43]" : "berry-text"}`}>{stat.value}</p>
              <p className="text-pretty max-w-40 text-right text-sm font-medium leading-5 text-[#675f57]">{stat.label}</p>
            </div>
          ))}
        </div>
      </section>

      <section id="products" className="mx-auto max-w-7xl px-5 py-20 md:py-24">
        <div className="mb-12 grid gap-6 md:grid-cols-[0.9fr_1.1fr] md:items-end">
          <div className="min-w-0">
            <p className="mb-3 text-[12px] font-semibold uppercase tracking-[0.24em] text-[#6d655d]">{t.products.label}</p>
            <h2 className="font-display text-balance text-4xl font-bold uppercase leading-[0.98] tracking-[-0.05em] berry-text md:text-6xl">{t.products.title}</h2>
          </div>
          <p className="text-pretty max-w-2xl text-lg leading-8 text-[#5f564e] md:ml-auto">{t.products.text}</p>
        </div>

        <div className="grid items-stretch gap-4 md:grid-cols-2 xl:grid-cols-4">
          {t.productList.map((item, index) => (
            <a href="#contact" key={item.name} onClick={() => handleProductClick(item.name)} className="group relative flex min-h-[340px] flex-col overflow-hidden rounded-[1.7rem] berry-border-soft bg-white p-6 shadow-sm transition hover:-translate-y-1 hover:shadow-xl hover:shadow-red-100/40">
              <div className="pointer-events-none absolute -right-8 -top-8 h-28 w-28 rounded-full opacity-10" style={{ background: `linear-gradient(135deg, ${productAccents[index]} 0%, #4f7b43 100%)` }} />
              <ProductVisual index={index} name={item.name} />
              <h3 className="font-display text-balance text-[25px] font-bold uppercase leading-[1.02] tracking-[-0.035em] berry-text">{item.name}</h3>
              <p className="text-pretty mt-4 text-[15px] leading-7 text-[#5f564e]">{item.detail}</p>
              <div className="mt-auto flex items-center justify-between gap-4 border-t border-[#d9e5d0] pt-5 text-sm">
                <span className="text-pretty text-[#6d655d]">{t.products.note}</span>
                <ArrowRight className="h-4 w-4 shrink-0 text-[#4f7b43] transition group-hover:translate-x-1" />
              </div>
            </a>
          ))}
        </div>
      </section>

      <section id="quality" className="overflow-hidden bg-gradient-to-br from-[#9c2329] via-[#7f1f25] to-[#4f7b43] py-20 text-white md:py-24">
        <div className="mx-auto grid max-w-7xl gap-12 px-5 lg:grid-cols-[0.9fr_1.1fr] lg:items-start">
          <div className="min-w-0 lg:sticky lg:top-28">
            <p className="mb-3 text-[12px] font-semibold uppercase tracking-[0.24em] text-white/70">{t.quality.label}</p>
            <h2 className="font-display text-balance text-4xl font-bold uppercase leading-[0.98] tracking-[-0.05em] md:text-6xl">{t.quality.title}</h2>
            <p className="text-pretty mt-6 text-lg leading-8 text-white/80">{t.quality.text}</p>
          </div>

          <div className="grid items-stretch gap-4 md:grid-cols-2">
            {t.quality.items.map((item, index) => {
              const Icon = qualityIcons[index];
              return (
                <div key={item.title} className="flex min-h-[270px] flex-col overflow-hidden rounded-[1.7rem] berry-border-dark bg-white/[0.10] p-6 backdrop-blur-sm">
                  <div className="mb-8 flex h-12 w-12 shrink-0 items-center justify-center rounded-full bg-white text-[#4f7b43]">
                    <Icon className="h-5 w-5" />
                  </div>
                  <h3 className="font-display text-balance text-[25px] font-bold uppercase leading-[1.02] tracking-[-0.035em]">{item.title}</h3>
                  <p className="text-pretty mt-4 leading-7 text-white/80">{item.text}</p>
                </div>
              );
            })}
          </div>
        </div>
      </section>

      <section id="markets" className="mx-auto max-w-7xl px-5 py-20 md:py-24">
        <div className="mb-12 max-w-3xl">
          <p className="mb-3 text-[12px] font-semibold uppercase tracking-[0.24em] text-[#6d655d]">{t.markets.label}</p>
          <h2 className="font-display text-balance text-4xl font-bold uppercase leading-[0.98] tracking-[-0.05em] berry-text md:text-6xl">{t.markets.title}</h2>
          <p className="text-pretty mt-6 text-lg leading-8 text-[#5f564e]">{t.markets.text}</p>
        </div>

        <div className="grid items-stretch gap-4 sm:grid-cols-2 lg:grid-cols-3">
          {t.markets.list.map((item, index) => {
            const Icon = marketIcons[index];
            return (
              <div key={item} className="flex min-h-[210px] flex-col overflow-hidden rounded-[1.7rem] berry-border-soft bg-white p-6">
                <div className="mb-8 flex h-12 w-12 shrink-0 items-center justify-center rounded-full bg-[#eef6ea] text-[#4f7b43]">
                  <Icon className="h-6 w-6" />
                </div>
                <p className="font-display text-balance text-[25px] font-bold uppercase leading-[1.02] tracking-[-0.035em] berry-text">{item}</p>
              </div>
            );
          })}
        </div>
      </section>

      <section id="about" className="border-y border-[#d9e5d0] bg-[#fffdfb]">
        <div className="mx-auto grid max-w-7xl gap-10 px-5 py-20 md:grid-cols-[0.7fr_1.3fr] md:items-center md:py-24">
          <div className="min-w-0">
            <p className="mb-3 text-[12px] font-semibold uppercase tracking-[0.24em] text-[#6d655d]">{t.about.label}</p>
            <h2 className="font-display text-balance text-4xl font-bold uppercase leading-[0.98] tracking-[-0.05em] berry-text md:text-6xl">{t.about.title}</h2>
          </div>
          <div className="overflow-hidden rounded-[2rem] berry-border-cream bg-gradient-to-br from-[#fff2ef] via-[#fffaf7] to-[#eef6ea] p-7 md:p-10">
            <p className="text-pretty text-[19px] leading-9 text-[#4f463f] md:text-[24px] md:leading-[1.65]">{t.about.text}</p>
          </div>
        </div>
      </section>

      <section id="contact" className="mx-auto grid max-w-7xl gap-12 px-5 py-20 md:grid-cols-[0.85fr_1.15fr] md:py-24">
        <div className="min-w-0">
          <p className="mb-3 text-[12px] font-semibold uppercase tracking-[0.24em] text-[#6d655d]">{t.contact.label}</p>
          <h2 className="font-display text-balance text-4xl font-bold uppercase leading-[0.98] tracking-[-0.05em] berry-text md:text-6xl">{t.contact.title}</h2>
          <p className="text-pretty mt-6 max-w-xl text-lg leading-8 text-[#5f564e]">{t.contact.text}</p>

          <div className="mt-9 space-y-3">
            <a href={`tel:${CONTACT.phoneLink}`} className="flex items-center gap-3 rounded-2xl berry-border-soft bg-white p-4 transition hover:bg-[#fff7f5]">
              <Phone className="h-5 w-5 shrink-0 text-[#4f7b43]" />
              <span className="break-words font-medium">{CONTACT.phoneDisplay}</span>
            </a>
            <a href={`mailto:${CONTACT.email}`} className="flex items-center gap-3 rounded-2xl berry-border-soft bg-white p-4 transition hover:bg-[#fff7f5]">
              <Mail className="h-5 w-5 shrink-0 text-[#4f7b43]" />
              <span className="break-all font-medium">{CONTACT.email}</span>
            </a>
          </div>
        </div>

        <div className="overflow-hidden rounded-[2rem] berry-border-soft bg-white p-5 shadow-xl shadow-red-100/30 md:p-8">
          <div className="mb-6 overflow-hidden rounded-3xl bg-gradient-to-r from-[#b52f33] to-[#4f7b43] p-6 text-white">
            <p className="text-sm text-white/75">{CONTACT.brand}</p>
            <p className="text-pretty mt-2 text-2xl font-semibold leading-8 tracking-tight">{t.contact.response}</p>
          </div>

          <div className="grid gap-4">
            <label className="grid gap-2 text-[12px] font-semibold uppercase tracking-[0.12em] text-[#5b524a]">
              {t.contact.name}
              <input className="w-full rounded-2xl berry-border-cream bg-[#fffaf7] px-4 py-4 text-[15px] outline-none transition focus:bg-white" value={form.name} onChange={(e) => setForm({ ...form, name: e.target.value })} />
            </label>

            <label className="grid gap-2 text-[12px] font-semibold uppercase tracking-[0.12em] text-[#5b524a]">
              {t.contact.contact}
              <input className="w-full rounded-2xl berry-border-cream bg-[#fffaf7] px-4 py-4 text-[15px] outline-none transition focus:bg-white" value={form.contact} onChange={(e) => setForm({ ...form, contact: e.target.value })} />
            </label>

            <label className="grid gap-2 text-[12px] font-semibold uppercase tracking-[0.12em] text-[#5b524a]">
              {t.contact.product}
              <select className="w-full rounded-2xl berry-border-cream bg-[#fffaf7] px-4 py-4 text-[15px] outline-none transition focus:bg-white" value={form.product} onChange={(e) => setForm({ ...form, product: e.target.value })}>
                <option value="">{t.contact.select}</option>
                {productNames.map((name) => <option key={name} value={name}>{name}</option>)}
                <option value={t.contact.mixed}>{t.contact.mixed}</option>
              </select>
            </label>

            <label className="grid gap-2 text-[12px] font-semibold uppercase tracking-[0.12em] text-[#5b524a]">
              {t.contact.message}
              <textarea className="min-h-32 w-full resize-none rounded-2xl berry-border-cream bg-[#fffaf7] px-4 py-4 text-[15px] outline-none transition focus:bg-white" value={form.message} onChange={(e) => setForm({ ...form, message: e.target.value })} />
            </label>

            <a href={`mailto:${CONTACT.email}?subject=${mailSubject}&body=${mailBody}`} className="block">
              <Button className="w-full rounded-full berry-button py-6 text-[12px] font-semibold uppercase tracking-[0.13em] text-white sm:text-[13px]">
                <Send className="mr-2 h-4 w-4 shrink-0" /> {t.contact.send}
              </Button>
            </a>
          </div>
        </div>
      </section>

      <footer className="border-t border-[#d9e5d0] bg-white px-5 py-8">
        <div className="mx-auto flex max-w-7xl flex-col justify-between gap-4 text-sm leading-6 text-[#6d655d] md:flex-row md:items-center">
          <div className="min-w-0">
            <p className="font-display text-sm font-bold uppercase tracking-[0.14em] berry-text">© {new Date().getFullYear()} {CONTACT.brand}</p>
            <p className="mt-1 text-pretty">{t.footer.line}</p>
          </div>
          <div className="flex min-w-0 flex-col gap-1 md:text-right">
            <p>{CONTACT.location[lang]}</p>
            <a href={`mailto:${CONTACT.email}`} className="break-all hover:text-[#5e7f47]">{CONTACT.email}</a>
          </div>
        </div>
      </footer>
    </main>
  );
}
