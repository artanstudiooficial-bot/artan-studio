import React, { useState, useEffect } from 'react';
import {
  ArrowRight,
  MessageCircle,
  Maximize2,
  X,
  ChevronDown,
  Instagram,
  MapPin,
  Phone,
  Clock,
  ArrowUpRight,
} from 'lucide-react';

/* ==========================================================================
   CONFIGURAÇÕES & DADOS DO ESTÚDIO
   ========================================================================== */

const STUDIO_CONFIG = {
  name: 'ABARR.',
  fullName: 'Abarr Tattoo',
  tagline: 'ESTÚDIO DE TATUAGEM AUTORAL',
  whatsappUrl: 'https://wa.me/5548992461205',
  instagramUrl: 'https://www.instagram.com/abarr_tattoo',
  instagramHandle: '@abarr_tattoo',
  phoneFormatted: '+55 (48) 99246-1205',
  location: 'Florianópolis, Santa Catarina · Brasil',
  hours: 'Segunda a Sábado, 10h às 20h (Atendimento Exclusivo com Hora Marcada)',
};

interface PortfolioItem {
  id: string;
  title: string;
  category: 'fineline' | 'darkart' | 'blackwork' | 'lettering';
  categoryLabel: string;
  image: string;
  alt: string;
  description: string;
  sessionTime: string;
  technique: string;
  healedMonths: number;
}

const PORTFOLIO_ITEMS: PortfolioItem[] = [
  {
    id: 'fineline-botanical',
    title: 'Flora & Geometria Cósmica',
    category: 'fineline',
    categoryLabel: 'Fine Line & Microrealismo',
    image: '/src/assets/images/tattoo_fineline_micro_1791466316805.jpg',
    alt: 'Tatuagem Fine Line botânica e geometria cósmica no antebraço',
    description:
      'Linhas ultra-finas de agulha 03RL com micro-sombreamento stippling. Projeto desenvolvido sob medida para a anatomia do antebraço.',
    sessionTime: '3h 40min',
    technique: 'Agulha 03RL · Pigmento Carbon Black',
    healedMonths: 4,
  },
  {
    id: 'darkart-corvo',
    title: 'Crânio de Corvo Barroco',
    category: 'darkart',
    categoryLabel: 'Dark Art & Neo-trad',
    image: '/src/assets/images/tattoo_darkart_neo_1791466331279.jpg',
    alt: 'Tatuagem Dark Art de crânio com detalhes barrocos no ombro',
    description:
      'Composição autoral com alto contraste, negros densos e sutil toque de pigmento carmim nos detalhes ornamentais.',
    sessionTime: '5h 15min',
    technique: 'Blackwork Denso · Sombreamento Opaque Grey',
    healedMonths: 6,
  },
  {
    id: 'blackwork-mandala',
    title: 'Mandala & Padrão Geométrico Sagrado',
    category: 'blackwork',
    categoryLabel: 'Blackwork & Geometria',
    image: '/src/assets/images/tattoo_blackwork_geo_1791466340220.jpg',
    alt: 'Tatuagem de mandala e geometria sagrada no peito e ombro',
    description:
      'Encaixe anatômico fluindo entre deltóide e peitoral. Precisão milimétrica em pontilhismo graduado e pretos sólidos.',
    sessionTime: '6h 30min',
    technique: 'Dotwork 05RL & Preenchimento Magnum',
    healedMonths: 8,
  },
  {
    id: 'studio-craft',
    title: 'Execução & Precisão em Agulha Única',
    category: 'fineline',
    categoryLabel: 'Precisão & Técnica',
    image: '/src/assets/images/hero_tattoo_machine_1791466303298.jpg',
    alt: 'Mão com luva preta segurando máquina rotativa executando traço',
    description:
      'Controle de profundidade dérmica com estabilidade estrita, prevenindo expansão ou estouro de traço ao longo dos anos.',
    sessionTime: 'Controle Cirúrgico',
    technique: 'Motor Direct Drive · Tensão 6.8V',
    healedMonths: 2,
  },
];

const PROCESS_STEPS = [
  {
    step: '01',
    title: 'Briefing & Consulta Inicial',
    description:
      'Conversamos pelo WhatsApp para entender sua ideia, referências estéticas, local anatômico e proporções desejadas.',
  },
  {
    step: '02',
    title: 'Criação Autoral & Validação',
    description:
      'Criamos uma arte exclusiva desenhada para seu corpo. Você visualiza a prévia, ajusta detalhes e aprova antes de qualquer agulhada.',
  },
  {
    step: '03',
    title: 'A Sessão no Estúdio',
    description:
      'Ambiente privativo e climatizado com música agradável, ergonomia de alto nível e todos os protocolos de assepsia rigorosamente aplicados.',
  },
  {
    step: '04',
    title: 'Guia Pós-Tatuagem & Acompanhamento',
    description:
      'Entregamos o protocolo completo de cicatrização (filme adesivo dérmico, pomadas indicadas) com suporte direto pelo WhatsApp até a cicatrização completa.',
  },
];

const FAQ_ITEMS = [
  {
    question: 'Como funciona o orçamento gratuito com a Abarr Tattoo?',
    answer:
      'É direto e sem burocracia. Você pode preencher o simulador aqui no site ou mandar uma mensagem no WhatsApp (+55 48 99246-1205) com a ideia, tamanho aproximado em centímetros e local do corpo. Nós analisamos a complexidade e retornamos com valores e opções de agenda.',
  },
  {
    question: 'As artes são realmente exclusivas ou vocês tatuam cópias da internet?',
    answer:
      'Nosso foco é arte autoral e exclusiva. Referências do Pinterest ou Instagram servem como ponto de partida conceitual, mas desenvolvemos uma peça única para você que respeita sua musculatura e anatomia.',
  },
  {
    question: 'É a minha primeira tatuagem. O que preciso saber sobre dor e preparação?',
    answer:
      'A sensação varia de acordo com o local, mas nossa equipe orienta cada detalhe: dormir bem na noite anterior, alimentação reforçada, hidratação da pele prévia e pausas programadas durante a sessão para seu conforto total.',
  },
  {
    question: 'Vocês fazem cobertura de tatuagem antiga (cover-up) ou de cicatrizes?',
    answer:
      'Sim. Avaliamos a viabilidade anatômica e tonalidade da tatuagem antiga ou cicatriz em uma consulta prévia para criar um projeto autoral que neutralize a arte anterior de forma estética e definitiva.',
  },
];

const BODY_PLACEMENTS = [
  'Antebraço',
  'Braço / Bíceps',
  'Ombro / Deltóide',
  'Peitoral',
  'Costela / Tronco',
  'Costas',
  'Coxa / Perna',
  'Panturrilha',
  'Punho / Mão',
  'Tornozelo / Pé',
];

const TATTOO_STYLES = [
  { id: 'fineline', label: 'Fine Line & Microrealismo', hint: 'Traços sutis e delicados' },
  { id: 'darkart', label: 'Dark Art & Neo-tradicional', hint: 'Contrastes e estética marcante' },
  { id: 'blackwork', label: 'Blackwork & Geometria', hint: 'Pretos sólidos e padronagens' },
  { id: 'lettering', label: 'Lettering & Caligrafia', hint: 'Fontes e composições autorais' },
  { id: 'coverup', label: 'Cobertura (Cover-up)', hint: 'Reforma ou cobertura de tattoo anterior' },
];

/* ==========================================================================
   COMPONENTE PRINCIPAL DO SITE (APP)
   ========================================================================== */

export default function App() {
  const [scrolled, setScrolled] = useState(false);
  const [activeCategory, setActiveCategory] = useState<string>('all');
  const [selectedModalItem, setSelectedModalItem] = useState<PortfolioItem | null>(null);
  const [selectedPlacement, setSelectedPlacement] = useState<string>('Antebraço');
  const [selectedStyle, setSelectedStyle] = useState<string>('fineline');
  const [sizeRange, setSizeRange] = useState<string>('10 a 15 cm');
  const [ideaText, setIdeaText] = useState<string>('');
  const [preferredPeriod, setPreferredPeriod] = useState<string>('Tarde');
  const [isCopied, setIsCopied] = useState<boolean>(false);
  const [openFaqIndex, setOpenFaqIndex] = useState<number | null>(0);

  useEffect(() => {
    const handleScroll = () => {
      setScrolled(window.scrollY > 20);
    };
    window.addEventListener('scroll', handleScroll);
    return () => window.removeEventListener('scroll', handleScroll);
  }, []);

  const scrollToQuote = (styleId?: string) => {
    if (styleId) {
      setSelectedStyle(styleId);
    }
    const el = document.getElementById('orcamento');
    if (el) {
      el.scrollIntoView({ behavior: 'smooth' });
    }
  };

  const categories = [
    { id: 'all', label: 'Todas as Obras' },
    { id: 'fineline', label: 'Fine Line & Micro' },
    { id: 'darkart', label: 'Dark Art & Neo' },
    { id: 'blackwork', label: 'Blackwork & Geometria' },
  ];

  const filteredPortfolio =
    activeCategory === 'all'
      ? PORTFOLIO_ITEMS
      : PORTFOLIO_ITEMS.filter((item) => item.category === activeCategory);

  const currentStyleObj =
    TATTOO_STYLES.find((s) => s.id === selectedStyle) || TATTOO_STYLES[0];

  const generateWhatsAppMessage = () => {
    let msg = `Olá, Abarr Tattoo! Gostaria de solicitar um orçamento gratuito para um projeto autoral:\n\n`;
    msg += `📍 Local do Corpo: ${selectedPlacement}\n`;
    msg += `🎨 Estilo Desejado: ${currentStyleObj.label}\n`;
    msg += `📐 Tamanho Estimado: ${sizeRange}\n`;
    msg += `⏰ Preferência de Horário: ${preferredPeriod}\n`;
    if (ideaText.trim()) {
      msg += `💡 Ideia/Conceito: "${ideaText.trim()}"\n\n`;
    } else {
      msg += `💡 Ideia/Conceito: (Tenho uma ideia inicial e gostaria de conversar para desenvolver)\n\n`;
    }
    msg += `Vi o site e gostaria de saber as datas disponíveis e estimativa de valor para essa arte exclusiva. Obrigado!`;
    return encodeURIComponent(msg);
  };

  const whatsappHref = `${STUDIO_CONFIG.whatsappUrl}?text=${generateWhatsAppMessage()}`;

  return (
    <div className="min-h-screen bg-[#0A0A0A] text-white selection:bg-[#E60000] selection:text-white font-epilogue antialiased overflow-x-hidden">
      
      {/* ----------------- NAVBAR ----------------- */}
      <header
        className={`fixed top-0 left-0 right-0 z-50 transition-all duration-300 ${
          scrolled
            ? 'bg-[#0A0A0A]/95 backdrop-blur-md border-b border-[#262626] py-3.5 sm:py-4 shadow-2xl'
            : 'bg-[#0A0A0A]/70 backdrop-blur-sm border-b border-white/5 py-4 sm:py-5'
        }`}
      >
        <div className="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
          <div className="flex items-center justify-between">
            <a href="#" className="flex items-center group focus:outline-none" aria-label="Abarr Tattoo">
              <span className="font-syne text-2xl sm:text-3xl font-extrabold tracking-widest text-[#E60000] drop-shadow-[0_2px_10px_rgba(230,0,0,0.35)]">
                {STUDIO_CONFIG.name}
              </span>
            </a>

            {/* Apenas no PC/Tablet - no telefone fica oculto */}
            <div className="hidden sm:block">
              <button
                onClick={() => scrollToQuote()}
                className="px-5 sm:px-6 py-2.5 sm:py-3 text-xs uppercase font-syne font-extrabold tracking-widest text-white border-2 border-white hover:border-[#E60000] hover:bg-[#E60000] transition-all duration-200 cursor-pointer shadow-lg shadow-black/40"
              >
                Orçamento Gratuito
              </button>
            </div>
          </div>
        </div>
      </header>

      <main>
        {/* ----------------- HERO SECTION ----------------- */}
        <section className="relative min-h-[88vh] flex items-center pt-24 pb-16 lg:pt-32 lg:pb-20 overflow-hidden border-b border-[#262626]">
          <div
            className="absolute top-1/4 -left-36 w-[500px] h-[500px] bg-[#E60000]/12 rounded-full blur-[160px] pointer-events-none"
            aria-hidden="true"
          />
          <div
            className="absolute bottom-10 right-0 w-[550px] h-[550px] bg-[#E60000]/10 rounded-full blur-[180px] pointer-events-none"
            aria-hidden="true"
          />

          <div className="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 w-full relative z-10">
            <div className="grid grid-cols-1 lg:grid-cols-12 gap-10 lg:gap-14 items-center">
              
              {/* Esquerda: Título encorpado + Texto + Botões empilhados */}
              <div className="lg:col-span-6 flex flex-col justify-center space-y-6 sm:space-y-7">
                <h1 className="font-syne text-3xl sm:text-4xl lg:text-[2.65rem] xl:text-[3.1rem] font-extrabold leading-[1.12] tracking-tight uppercase text-white text-balance drop-shadow-md">
                  Arte Exclusiva na Pele. <br />
                  <span className="text-white block mt-1 sm:mt-1.5">
                    Projetos Autorais e&nbsp;Únicos.
                  </span>
                </h1>

                <p className="font-epilogue text-sm sm:text-base lg:text-lg text-neutral-300 leading-relaxed max-w-xl font-normal">
                  Transforme sua ideia em uma tatuagem marcante com a Abarr Tattoo. Agende uma consulta e receba um orçamento gratuito, direto com nosso estúdio.
                </p>

                {/* Botões verticais (um abaixo do outro) */}
                <div className="flex flex-col items-stretch sm:items-start gap-3.5 pt-1 w-full max-w-md">
                  <button
                    onClick={() => scrollToQuote()}
                    className="w-full sm:w-auto inline-flex items-center justify-center gap-3 px-8 py-4 text-xs sm:text-sm uppercase font-syne font-extrabold tracking-widest text-white border-2 border-white hover:border-[#E60000] hover:bg-[#E60000] transition-all duration-200 cursor-pointer shadow-xl shadow-black/50"
                  >
                    <span>Fazer Orçamento Gratuito</span>
                    <ArrowRight className="w-4 h-4 group-hover:translate-x-1.5 transition-transform" />
                  </button>

                  <a
                    href={STUDIO_CONFIG.whatsappUrl}
                    target="_blank"
                    rel="noopener noreferrer"
                    className="w-full sm:w-auto inline-flex items-center justify-center gap-3 px-8 py-4 text-xs sm:text-sm uppercase font-syne font-extrabold tracking-widest text-white border-2 border-white/80 hover:border-white bg-[#0A0A0A] hover:bg-white hover:text-black transition-all duration-200"
                  >
                    <MessageCircle className="w-4 h-4 text-[#E60000] group-hover:text-black transition-colors" />
                    <span>Iniciar Orçamento pelo WhatsApp</span>
                  </a>
                </div>
              </div>

              {/* Direita: Fotografia com bordas vermelhas e sem textos por cima */}
              <div className="lg:col-span-6 relative mt-4 lg:mt-0">
                <div className="relative mx-auto max-w-md sm:max-w-lg lg:max-w-none">
                  <div className="relative overflow-hidden border border-[#262626] bg-[#121212] group shadow-2xl">
                    <div className="absolute inset-0 border-2 border-transparent group-hover:border-[#E60000] transition-colors duration-300 pointer-events-none z-20" />
                    
                    <img
                      src="/src/assets/images/hero_tattoo_machine_1791466303298.jpg"
                      alt="Close-up fotográfico de estúdio: máquina de tatuagem de precisão empunhada com luva cirúrgica preta"
                      referrerPolicy="no-referrer"
                      className="w-full h-auto max-h-[480px] sm:max-h-[520px] lg:max-h-[550px] aspect-[4/3] sm:aspect-[4/3] lg:aspect-[4/3.8] object-cover filter contrast-[1.08] brightness-95 group-hover:scale-[1.02] transition-transform duration-700 ease-out"
                    />

                    <div className="absolute inset-0 bg-gradient-to-t from-black/40 via-transparent to-transparent pointer-events-none" />
                  </div>

                  {/* Detalhes geométricos nas bordas em vermelho */}
                  <div
                    className="absolute -bottom-3 -right-3 w-14 h-14 border-r-2 border-b-2 border-[#E60000] pointer-events-none"
                    aria-hidden="true"
                  />
                  <div
                    className="absolute -top-3 -left-3 w-14 h-14 border-l-2 border-t-2 border-[#E60000]/80 pointer-events-none"
                    aria-hidden="true"
                  />
                </div>
              </div>

            </div>
          </div>
        </section>

        {/* ----------------- PORTFÓLIO BENTO GRID ----------------- */}
        <section id="portfolio" className="py-24 sm:py-32 bg-[#0A0A0A] border-b border-[#262626] relative">
          <div className="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
            <div className="flex flex-col md:flex-row md:items-end justify-between mb-12 sm:mb-16 gap-6">
              <div className="space-y-3">
                <div className="flex items-center gap-2">
                  <span className="w-2 h-2 bg-[#E60000]" />
                  <p className="text-xs font-syne font-bold uppercase tracking-[0.2em] text-[#E60000]">
                    Portfólio Selecionado
                  </p>
                </div>
                <h2 className="font-syne text-3xl sm:text-4xl lg:text-5xl font-bold tracking-tight text-white text-balance">
                  Identidade e Precisão.
                </h2>
                <p className="font-epilogue text-neutral-400 text-sm sm:text-base max-w-xl">
                  Projetos exclusivos concebidos do zero para a anatomia de cada cliente. Sem reproduções da internet ou cópias genéricas.
                </p>
              </div>

              {/* Filtro interativo */}
              <div className="flex flex-wrap items-center gap-1.5 p-1 bg-[#121212] border border-[#262626]">
                {categories.map((cat) => {
                  const isActive = activeCategory === cat.id;
                  return (
                    <button
                      key={cat.id}
                      onClick={() => setActiveCategory(cat.id)}
                      className={`px-3 sm:px-4 py-2 text-xs font-syne uppercase tracking-wider font-semibold transition-all cursor-pointer whitespace-nowrap ${
                        isActive
                          ? 'bg-white text-black shadow-md'
                          : 'text-neutral-400 hover:text-white hover:bg-neutral-800/50'
                      }`}
                    >
                      {cat.label}
                    </button>
                  );
                })}
              </div>
            </div>

            {/* Bento Grid */}
            <div className="grid grid-cols-1 md:grid-cols-12 gap-6 sm:gap-8">
              
              {/* Card 1 */}
              <div
                onClick={() => setSelectedModalItem(PORTFOLIO_ITEMS[0])}
                className="md:col-span-7 group relative bg-[#121212] border border-[#262626] hover:border-[#E60000]/60 transition-all duration-300 overflow-hidden cursor-pointer flex flex-col justify-between"
              >
                <div className="relative aspect-[4/3] sm:aspect-[16/10] overflow-hidden">
                  <img
                    src={PORTFOLIO_ITEMS[0].image}
                    alt={PORTFOLIO_ITEMS[0].alt}
                    referrerPolicy="no-referrer"
                    className="w-full h-full object-cover object-top group-hover:scale-105 transition-transform duration-700 ease-out brightness-95"
                  />
                  <div className="absolute inset-0 bg-gradient-to-t from-[#121212] via-[#121212]/30 to-transparent" />
                  <div className="absolute top-4 right-4 p-2 bg-[#0A0A0A]/80 border border-[#262626] text-white opacity-0 group-hover:opacity-100 transition-opacity">
                    <Maximize2 className="w-4 h-4 text-[#E60000]" />
                  </div>
                </div>

                <div className="p-6 sm:p-8 space-y-3 relative -mt-12 sm:-mt-16 z-10">
                  <div className="flex items-center gap-2 text-xs text-neutral-400 font-epilogue">
                    <span className="text-[#E60000] font-syne font-bold uppercase tracking-wider">
                      {PORTFOLIO_ITEMS[0].categoryLabel}
                    </span>
                    <span>·</span>
                    <span>Cicatrizada há {PORTFOLIO_ITEMS[0].healedMonths} meses</span>
                  </div>
                  <h3 className="font-syne text-2xl sm:text-3xl font-bold text-white group-hover:text-[#E60000] transition-colors">
                    {PORTFOLIO_ITEMS[0].title}
                  </h3>
                  <p className="font-epilogue text-neutral-300 text-sm leading-relaxed">
                    {PORTFOLIO_ITEMS[0].description}
                  </p>
                </div>
              </div>

              {/* Card 2 */}
              <div
                onClick={() => setSelectedModalItem(PORTFOLIO_ITEMS[1])}
                className="md:col-span-5 group relative bg-[#121212] border border-[#262626] hover:border-[#E60000]/60 transition-all duration-300 overflow-hidden cursor-pointer flex flex-col justify-between"
              >
                <div className="relative aspect-[3/4] sm:aspect-[4/4] overflow-hidden">
                  <img
                    src={PORTFOLIO_ITEMS[1].image}
                    alt={PORTFOLIO_ITEMS[1].alt}
                    referrerPolicy="no-referrer"
                    className="w-full h-full object-cover group-hover:scale-105 transition-transform duration-700 ease-out brightness-95"
                  />
                  <div className="absolute inset-0 bg-gradient-to-t from-[#121212] via-[#121212]/30 to-transparent" />
                  <div className="absolute top-4 right-4 p-2 bg-[#0A0A0A]/80 border border-[#262626] text-white opacity-0 group-hover:opacity-100 transition-opacity">
                    <Maximize2 className="w-4 h-4 text-[#E60000]" />
                  </div>
                </div>

                <div className="p-6 sm:p-8 space-y-3 relative -mt-12 z-10">
                  <div className="flex items-center gap-2 text-xs text-neutral-400 font-epilogue">
                    <span className="text-[#E60000] font-syne font-bold uppercase tracking-wider">
                      {PORTFOLIO_ITEMS[1].categoryLabel}
                    </span>
                    <span>·</span>
                    <span>{PORTFOLIO_ITEMS[1].sessionTime}</span>
                  </div>
                  <h3 className="font-syne text-2xl font-bold text-white group-hover:text-[#E60000] transition-colors">
                    {PORTFOLIO_ITEMS[1].title}
                  </h3>
                  <p className="font-epilogue text-neutral-300 text-sm leading-relaxed">
                    {PORTFOLIO_ITEMS[1].description}
                  </p>
                </div>
              </div>

              {/* Card 3 */}
              <div
                onClick={() => setSelectedModalItem(PORTFOLIO_ITEMS[2])}
                className="md:col-span-6 group relative bg-[#121212] border border-[#262626] hover:border-[#E60000]/60 transition-all duration-300 overflow-hidden cursor-pointer flex flex-col justify-between"
              >
                <div className="relative aspect-[4/3] overflow-hidden">
                  <img
                    src={PORTFOLIO_ITEMS[2].image}
                    alt={PORTFOLIO_ITEMS[2].alt}
                    referrerPolicy="no-referrer"
                    className="w-full h-full object-cover group-hover:scale-105 transition-transform duration-700 ease-out brightness-95"
                  />
                  <div className="absolute inset-0 bg-gradient-to-t from-[#121212] via-[#121212]/30 to-transparent" />
                  <div className="absolute top-4 right-4 p-2 bg-[#0A0A0A]/80 border border-[#262626] text-white opacity-0 group-hover:opacity-100 transition-opacity">
                    <Maximize2 className="w-4 h-4 text-[#E60000]" />
                  </div>
                </div>

                <div className="p-6 sm:p-8 space-y-3 relative -mt-10 z-10">
                  <div className="flex items-center gap-2 text-xs text-neutral-400 font-epilogue">
                    <span className="text-[#E60000] font-syne font-bold uppercase tracking-wider">
                      {PORTFOLIO_ITEMS[2].categoryLabel}
                    </span>
                    <span>·</span>
                    <span>Cicatrizada há {PORTFOLIO_ITEMS[2].healedMonths} meses</span>
                  </div>
                  <h3 className="font-syne text-2xl font-bold text-white group-hover:text-[#E60000] transition-colors">
                    {PORTFOLIO_ITEMS[2].title}
                  </h3>
                  <p className="font-epilogue text-neutral-300 text-sm leading-relaxed">
                    {PORTFOLIO_ITEMS[2].description}
                  </p>
                </div>
              </div>

              {/* Card 4 */}
              <div
                onClick={() => setSelectedModalItem(PORTFOLIO_ITEMS[3])}
                className="md:col-span-6 group relative bg-[#121212] border border-[#262626] hover:border-[#E60000]/60 transition-all duration-300 overflow-hidden cursor-pointer flex flex-col justify-between"
              >
                <div className="relative aspect-[4/3] overflow-hidden">
                  <img
                    src={PORTFOLIO_ITEMS[3].image}
                    alt={PORTFOLIO_ITEMS[3].alt}
                    referrerPolicy="no-referrer"
                    className="w-full h-full object-cover group-hover:scale-105 transition-transform duration-700 ease-out brightness-95"
                  />
                  <div className="absolute inset-0 bg-gradient-to-t from-[#121212] via-[#121212]/30 to-transparent" />
                  <div className="absolute top-4 right-4 p-2 bg-[#0A0A0A]/80 border border-[#262626] text-white opacity-0 group-hover:opacity-100 transition-opacity">
                    <Maximize2 className="w-4 h-4 text-[#E60000]" />
                  </div>
                </div>

                <div className="p-6 sm:p-8 space-y-3 relative -mt-10 z-10">
                  <div className="flex items-center gap-2 text-xs text-neutral-400 font-epilogue">
                    <span className="text-[#E60000] font-syne font-bold uppercase tracking-wider">
                      {PORTFOLIO_ITEMS[3].categoryLabel}
                    </span>
                    <span>·</span>
                    <span>Precisão Dérmica</span>
                  </div>
                  <h3 className="font-syne text-2xl font-bold text-white group-hover:text-[#E60000] transition-colors">
                    {PORTFOLIO_ITEMS[3].title}
                  </h3>
                  <p className="font-epilogue text-neutral-300 text-sm leading-relaxed">
                    {PORTFOLIO_ITEMS[3].description}
                  </p>
                </div>
              </div>

            </div>
          </div>

          {/* Modal de Detalhe da Obra */}
          {selectedModalItem && (
            <div
              role="dialog"
              aria-modal="true"
              className="fixed inset-0 z-50 flex items-center justify-center p-4 sm:p-6 bg-black/90 backdrop-blur-md"
              onClick={() => setSelectedModalItem(null)}
            >
              <div
                className="relative w-full max-w-4xl bg-[#121212] border border-[#262626] overflow-hidden shadow-2xl max-h-[90vh] flex flex-col md:flex-row"
                onClick={(e) => e.stopPropagation()}
              >
                <button
                  onClick={() => setSelectedModalItem(null)}
                  className="absolute top-4 right-4 z-20 p-2 bg-[#0A0A0A]/90 text-white hover:text-[#E60000] border border-[#262626] cursor-pointer"
                  aria-label="Fechar modal"
                >
                  <X className="w-5 h-5" />
                </button>

                <div className="md:w-1/2 bg-[#0A0A0A] flex items-center justify-center overflow-hidden">
                  <img
                    src={selectedModalItem.image}
                    alt={selectedModalItem.alt}
                    referrerPolicy="no-referrer"
                    className="w-full h-full max-h-[50vh] md:max-h-[80vh] object-cover"
                  />
                </div>

                <div className="md:w-1/2 p-6 sm:p-8 flex flex-col justify-between overflow-y-auto space-y-6">
                  <div className="space-y-4">
                    <div className="flex items-center gap-2 text-xs text-neutral-400 font-epilogue">
                      <span className="text-[#E60000] font-syne font-bold uppercase tracking-wider">
                        {selectedModalItem.categoryLabel}
                      </span>
                      <span>·</span>
                      <span>Cicatrizada há {selectedModalItem.healedMonths} meses</span>
                    </div>

                    <h3 className="font-syne text-2xl sm:text-3xl font-bold text-white">
                      {selectedModalItem.title}
                    </h3>

                    <p className="font-epilogue text-neutral-300 text-sm leading-relaxed">
                      {selectedModalItem.description}
                    </p>

                    <div className="pt-4 border-t border-[#262626] space-y-2 text-xs">
                      <div className="p-3 bg-[#0A0A0A] border border-[#262626]">
                        <span className="text-neutral-500 block">Tempo de Sessão</span>
                        <span className="font-syne font-semibold text-white">{selectedModalItem.sessionTime}</span>
                      </div>
                      <div className="p-3 bg-[#0A0A0A] border border-[#262626]">
                        <span className="text-neutral-500 block">Equipamento & Técnica</span>
                        <span className="font-epilogue text-neutral-300">{selectedModalItem.technique}</span>
                      </div>
                    </div>
                  </div>

                  <div className="pt-4 border-t border-[#262626] flex gap-3">
                    <button
                      onClick={() => {
                        const style = selectedModalItem.category;
                        setSelectedModalItem(null);
                        scrollToQuote(style);
                      }}
                      className="flex-1 py-3 text-xs uppercase font-syne font-bold tracking-wider text-white border border-white hover:border-[#E60000] hover:bg-[#E60000] transition-colors text-center cursor-pointer"
                    >
                      Orçar Esse Estilo
                    </button>
                    <a
                      href={`${STUDIO_CONFIG.whatsappUrl}?text=${encodeURIComponent(
                        `Olá! Gostei do projeto "${selectedModalItem.title}" no site da Abarr Tattoo e quero um orçamento autoral nesse estilo.`
                      )}`}
                      target="_blank"
                      rel="noopener noreferrer"
                      className="inline-flex items-center justify-center gap-2 px-4 py-3 text-xs uppercase font-syne font-bold tracking-wider bg-[#E60000] text-white hover:bg-[#CC0000] transition-colors"
                    >
                      <MessageCircle className="w-4 h-4" />
                      <span>WhatsApp</span>
                    </a>
                  </div>
                </div>
              </div>
            </div>
          )}
        </section>

        {/* ----------------- PROCESSO AUTORAL ----------------- */}
        <section id="processo" className="py-24 sm:py-32 bg-[#0A0A0A] border-b border-[#262626] relative">
          <div className="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
            <div className="max-w-3xl mb-16 space-y-4">
              <div className="flex items-center gap-2">
                <span className="w-2 h-2 bg-[#E60000]" />
                <p className="text-xs font-syne font-bold uppercase tracking-[0.2em] text-[#E60000]">
                  Metodologia de Estúdio
                </p>
              </div>
              <h2 className="font-syne text-3xl sm:text-4xl lg:text-5xl font-bold tracking-tight text-white text-balance">
                Do Conceito à Pele: O Processo Autoral.
              </h2>
              <p className="font-epilogue text-neutral-300 text-base sm:text-lg leading-relaxed">
                Cada traço é planejado especificamente para sua curvatura muscular, garantindo um resultado marcante que envelhece com precisão.
              </p>
            </div>

            <div className="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-4 gap-6 sm:gap-8">
              {PROCESS_STEPS.map((step) => (
                <div
                  key={step.step}
                  className="p-7 sm:p-8 bg-[#121212] border border-[#262626] relative flex flex-col justify-between space-y-8 group hover:border-[#E60000]/60 transition-colors"
                >
                  <div className="space-y-4">
                    <span className="font-syne text-3xl font-extrabold text-[#E60000] block">
                      {step.step}.
                    </span>
                    <h3 className="font-syne text-xl font-bold text-white">
                      {step.title}
                    </h3>
                    <p className="font-epilogue text-xs sm:text-sm text-neutral-400 leading-relaxed">
                      {step.description}
                    </p>
                  </div>
                  <div className="pt-4 border-t border-[#262626]/80 flex items-center justify-between text-[11px] font-syne uppercase tracking-wider text-neutral-500">
                    <span>Etapa {step.step}</span>
                    <span className="text-[#E60000]">Exclusivo</span>
                  </div>
                </div>
              ))}
            </div>
          </div>
        </section>

        {/* ----------------- SIMULADOR DE ORÇAMENTO (COM NEON VERMELHO) ----------------- */}
        <section id="orcamento" className="py-24 sm:py-32 bg-[#0A0A0A] border-b border-[#262626] relative overflow-hidden">
          {/* Luz Neon Vermelha de Fundo */}
          <div
            className="absolute top-1/2 left-1/2 -translate-x-1/2 -translate-y-1/2 w-[650px] sm:w-[850px] h-[550px] sm:h-[700px] bg-[#E60000]/22 rounded-full blur-[140px] sm:blur-[180px] pointer-events-none"
            aria-hidden="true"
          />
          <div
            className="absolute -bottom-24 left-1/2 -translate-x-1/2 w-[400px] h-[250px] bg-[#E60000]/30 rounded-full blur-[120px] pointer-events-none"
            aria-hidden="true"
          />

          <div className="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 relative z-10">
            <div className="max-w-3xl mb-12 sm:mb-16 space-y-3 text-center mx-auto">
              <div className="inline-flex items-center gap-2">
                <span className="w-2.5 h-2.5 bg-[#E60000] shadow-[0_0_12px_#E60000]" />
                <p className="text-xs font-syne font-extrabold uppercase tracking-[0.25em] text-[#E60000]">
                  Simulação de Orçamento
                </p>
              </div>
              <h2 className="font-syne text-3xl sm:text-5xl font-extrabold tracking-tight uppercase text-white text-balance drop-shadow-md">
                Simule & Solicite seu Orçamento Gratuito.
              </h2>
              <p className="font-epilogue text-neutral-300 text-sm sm:text-base max-w-xl mx-auto">
                Personalize os parâmetros da sua tatuagem abaixo e envie diretamente para os tatuadores da Abarr Tattoo via WhatsApp com um clique.
              </p>
            </div>

            <div className="max-w-4xl mx-auto bg-[#121212]/95 backdrop-blur-xl border border-[#262626] hover:border-[#E60000]/50 p-6 sm:p-10 lg:p-12 shadow-[0_0_50px_rgba(230,0,0,0.15)] transition-all duration-300">
              <form
                onSubmit={(e) => {
                  e.preventDefault();
                  window.open(whatsappHref, '_blank');
                }}
                className="space-y-8"
              >
                {/* 1. Local do corpo */}
                <div className="space-y-3">
                  <label className="block text-xs font-syne font-extrabold uppercase tracking-widest text-neutral-300">
                    1. Onde será a tatuagem no seu corpo?
                  </label>
                  <div className="grid grid-cols-2 sm:grid-cols-3 md:grid-cols-5 gap-2">
                    {BODY_PLACEMENTS.map((placement) => {
                      const isSelected = selectedPlacement === placement;
                      return (
                        <button
                          key={placement}
                          type="button"
                          onClick={() => setSelectedPlacement(placement)}
                          className={`px-3 py-2.5 text-xs font-epilogue transition-all text-center border cursor-pointer ${
                            isSelected
                              ? 'border-[#E60000] bg-[#E60000]/20 text-white font-semibold shadow-[0_0_15px_rgba(230,0,0,0.3)]'
                              : 'border-[#262626] bg-[#0A0A0A] text-neutral-400 hover:text-white hover:border-neutral-700'
                          }`}
                        >
                          {placement}
                        </button>
                      );
                    })}
                  </div>
                </div>

                {/* 2. Estilo */}
                <div className="space-y-3">
                  <label className="block text-xs font-syne font-extrabold uppercase tracking-widest text-neutral-300">
                    2. Qual o estilo artístico principal?
                  </label>
                  <div className="grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-3 gap-3">
                    {TATTOO_STYLES.map((style) => {
                      const isSelected = selectedStyle === style.id;
                      return (
                        <button
                          key={style.id}
                          type="button"
                          onClick={() => setSelectedStyle(style.id)}
                          className={`p-3.5 border text-left transition-all cursor-pointer flex flex-col justify-between ${
                            isSelected
                              ? 'border-[#E60000] bg-[#E60000]/20 shadow-[0_0_15px_rgba(230,0,0,0.25)]'
                              : 'border-[#262626] bg-[#0A0A0A] hover:border-neutral-700'
                          }`}
                        >
                          <span className={`text-xs font-syne font-bold ${isSelected ? 'text-white' : 'text-neutral-300'}`}>
                            {style.label}
                          </span>
                          <span className="text-[11px] font-epilogue text-neutral-500 mt-1">
                            {style.hint}
                          </span>
                        </button>
                      );
                    })}
                  </div>
                </div>

                {/* 3. Tamanho & Horário */}
                <div className="grid grid-cols-1 md:grid-cols-2 gap-6">
                  <div className="space-y-3">
                    <label className="block text-xs font-syne font-extrabold uppercase tracking-widest text-neutral-300">
                      3. Tamanho aproximado
                    </label>
                    <div className="space-y-2">
                      {[
                        { label: '5 a 8 cm (Pequena/Delicada)', value: '5 a 8 cm' },
                        { label: '10 a 15 cm (Média)', value: '10 a 15 cm' },
                        { label: '15 a 25 cm (Grande)', value: '15 a 25 cm' },
                        { label: 'Fechamento de Área / Projeto Amplo', value: 'Fechamento / Projeto Amplo' },
                      ].map((opt) => (
                        <label
                          key={opt.value}
                          className={`flex items-center gap-3 p-3 border cursor-pointer transition-colors ${
                            sizeRange === opt.value
                              ? 'border-[#E60000] bg-[#E60000]/20 text-white'
                              : 'border-[#262626] bg-[#0A0A0A] text-neutral-400 hover:text-white hover:border-neutral-700'
                          }`}
                        >
                          <input
                            type="radio"
                            name="size"
                            value={opt.value}
                            checked={sizeRange === opt.value}
                            onChange={() => setSizeRange(opt.value)}
                            className="accent-[#E60000]"
                          />
                          <span className="text-xs font-epilogue">{opt.label}</span>
                        </label>
                      ))}
                    </div>
                  </div>

                  <div className="space-y-3">
                    <label className="block text-xs font-syne font-extrabold uppercase tracking-widest text-neutral-300">
                      4. Preferência de horário
                    </label>
                    <div className="grid grid-cols-3 gap-2">
                      {['Manhã (10h-14h)', 'Tarde (14h-18h)', 'Sábado'].map((period) => (
                        <button
                          key={period}
                          type="button"
                          onClick={() => setPreferredPeriod(period)}
                          className={`p-3 text-xs font-epilogue text-center border cursor-pointer transition-colors ${
                            preferredPeriod === period
                              ? 'border-[#E60000] bg-[#E60000]/20 text-white font-semibold shadow-[0_0_12px_rgba(230,0,0,0.3)]'
                              : 'border-[#262626] bg-[#0A0A0A] text-neutral-400 hover:text-white'
                          }`}
                        >
                          {period}
                        </button>
                      ))}
                    </div>

                    <div className="pt-3 space-y-2">
                      <label className="block text-xs font-syne font-extrabold uppercase tracking-widest text-neutral-300">
                        5. Descreva sua ideia ou conceito (Opcional)
                      </label>
                      <textarea
                        rows={3}
                        value={ideaText}
                        onChange={(e) => setIdeaText(e.target.value)}
                        placeholder="Ex: Tatuagem botânica com traços finos no antebraço interno..."
                        className="w-full bg-[#0A0A0A] border border-[#262626] p-3 text-xs font-epilogue text-white placeholder-neutral-600 focus:outline-none focus:border-[#E60000] transition-colors resize-none"
                      />
                    </div>
                  </div>
                </div>

                {/* Prévia da Mensagem */}
                <div className="p-4 sm:p-5 bg-[#0A0A0A] border border-[#262626] space-y-2">
                  <div className="flex items-center justify-between text-xs text-neutral-400 font-epilogue">
                    <div className="flex items-center gap-2 text-[#E60000] font-syne font-bold uppercase tracking-wider">
                      <MessageCircle className="w-3.5 h-3.5" />
                      <span>Prévia do Envio para o WhatsApp</span>
                    </div>
                    <span className="text-[11px] text-neutral-500">+55 48 99246-1205</span>
                  </div>
                  <p className="text-xs font-epilogue text-neutral-300 bg-neutral-950 p-3 border border-neutral-900 leading-relaxed font-mono whitespace-pre-line text-neutral-400">
                    Local: <span className="text-white">{selectedPlacement}</span> · Estilo: <span className="text-white">{currentStyleObj.label}</span> · Tamanho: <span className="text-white">{sizeRange}</span> · Turno: <span className="text-white">{preferredPeriod}</span>
                    {ideaText ? ` · Ideia: "${ideaText}"` : ''}
                  </p>
                </div>

                {/* Botões de Ação */}
                <div className="pt-2 flex flex-col sm:flex-row items-stretch sm:items-center gap-4">
                  <a
                    href={whatsappHref}
                    target="_blank"
                    rel="noopener noreferrer"
                    className="flex-1 inline-flex items-center justify-center gap-3 px-8 py-4.5 text-xs sm:text-sm uppercase font-syne font-extrabold tracking-wider bg-[#E60000] hover:bg-[#CC0000] text-white transition-all shadow-[0_0_30px_rgba(230,0,0,0.4)] text-center cursor-pointer"
                  >
                    <MessageCircle className="w-4 h-4" />
                    <span>Enviar Orçamento para o WhatsApp (+55 48 99246-1205)</span>
                    <ArrowRight className="w-4 h-4" />
                  </a>

                  <button
                    type="button"
                    onClick={() => {
                      navigator.clipboard.writeText(
                        `Local: ${selectedPlacement} | Estilo: ${currentStyleObj.label} | Tamanho: ${sizeRange} | Ideia: ${ideaText || 'Ideia a definir'}`
                      );
                      setIsCopied(true);
                      setTimeout(() => setIsCopied(false), 3000);
                    }}
                    className="px-6 py-4.5 text-xs uppercase font-syne font-bold tracking-wider text-white border border-white/60 hover:border-white transition-colors cursor-pointer text-center"
                  >
                    {isCopied ? 'Resumo Copiado!' : 'Copiar Resumo'}
                  </button>
                </div>
              </form>
            </div>
          </div>
        </section>

        {/* ----------------- PERGUNTAS FREQUENTES ----------------- */}
        <section id="duvidas" className="py-24 sm:py-32 bg-[#0A0A0A] border-b border-[#262626] relative">
          <div className="max-w-5xl mx-auto px-4 sm:px-6 lg:px-8">
            <div className="text-center max-w-2xl mx-auto mb-16 space-y-4">
              <div className="inline-flex items-center gap-2">
                <span className="w-2 h-2 bg-[#E60000]" />
                <p className="text-xs font-syne font-bold uppercase tracking-[0.2em] text-[#E60000]">
                  Transparência & Cuidados
                </p>
              </div>
              <h2 className="font-syne text-3xl sm:text-4xl lg:text-5xl font-bold tracking-tight text-white text-balance">
                Perguntas Frequentes.
              </h2>
              <p className="font-epilogue text-neutral-400 text-sm sm:text-base">
                Tire suas dúvidas sobre o processo autoral, valores e cuidados antes da sua sessão.
              </p>
            </div>

            <div className="space-y-4">
              {FAQ_ITEMS.map((item, idx) => {
                const isOpen = openFaqIndex === idx;
                return (
                  <div key={idx} className="bg-[#121212] border border-[#262626] transition-colors">
                    <button
                      type="button"
                      onClick={() => setOpenFaqIndex(isOpen ? null : idx)}
                      className="w-full p-6 text-left flex items-center justify-between gap-4 cursor-pointer focus:outline-none"
                    >
                      <span className="font-syne text-base sm:text-lg font-bold text-white pr-4">
                        {item.question}
                      </span>
                      <div className={`p-1 text-neutral-400 transition-transform duration-200 shrink-0 ${isOpen ? 'rotate-180 text-[#E60000]' : ''}`}>
                        <ChevronDown className="w-5 h-5" />
                      </div>
                    </button>
                    {isOpen && (
                      <div className="px-6 pb-6 pt-1 text-sm font-epilogue text-neutral-300 leading-relaxed border-t border-[#262626]/50">
                        <p>{item.answer}</p>
                      </div>
                    )}
                  </div>
                );
              })}
            </div>
          </div>
        </section>
      </main>

      {/* ----------------- FOOTER ----------------- */}
      <footer className="bg-[#0A0A0A] border-t border-[#262626] relative overflow-hidden">
        {/* Bloco de conversão centralizado */}
        <div className="py-20 sm:py-28 px-4 sm:px-6 lg:px-8 border-b border-[#262626] relative">
          <div
            className="absolute top-1/2 left-1/2 -translate-x-1/2 -translate-y-1/2 w-[550px] h-[350px] bg-[#E60000]/10 rounded-full blur-[140px] pointer-events-none"
            aria-hidden="true"
          />

          <div className="max-w-4xl mx-auto text-center space-y-6 relative z-10">
            <div className="inline-flex items-center gap-2">
              <span className="w-2 h-2 bg-[#E60000]" />
              <span className="text-xs font-syne font-bold uppercase tracking-[0.25em] text-[#E60000]">
                Inicie Sua Transformação
              </span>
            </div>

            <h2 className="font-syne text-3xl sm:text-4xl lg:text-5xl font-bold tracking-tight text-white text-balance">
              Sua ideia merece uma arte exclusiva e irrepetível.
            </h2>

            <p className="font-epilogue text-neutral-300 text-base sm:text-lg max-w-2xl mx-auto leading-relaxed">
              Consulte disponibilidade de agenda, tire dúvidas técnicas e receba uma orientação autoral sob medida diretamente com nossos tatuadores.
            </p>

            <div className="pt-4 flex flex-col sm:flex-row items-center justify-center gap-4">
              <a
                href={STUDIO_CONFIG.whatsappUrl}
                target="_blank"
                rel="noopener noreferrer"
                className="w-full sm:w-auto inline-flex items-center justify-center gap-3 px-8 py-4 text-xs sm:text-sm uppercase font-syne font-bold tracking-wider bg-[#E60000] hover:bg-[#CC0000] text-white transition-all shadow-xl shadow-[#E60000]/30 cursor-pointer"
              >
                <MessageCircle className="w-4 h-4" />
                <span>Iniciar Orçamento pelo WhatsApp</span>
                <ArrowUpRight className="w-4 h-4" />
              </a>

              <button
                onClick={() => scrollToQuote()}
                className="w-full sm:w-auto px-8 py-4 text-xs sm:text-sm uppercase font-syne font-bold tracking-wider text-white border-2 border-white hover:border-[#E60000] hover:bg-white hover:text-black transition-all cursor-pointer"
              >
                Simular Orçamento no Site
              </button>
            </div>
          </div>
        </div>

        {/* Rodapé institucional com Instagram e WhatsApp */}
        <div className="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 py-16">
          <div className="grid grid-cols-1 md:grid-cols-12 gap-10 lg:gap-14">
            <div className="md:col-span-5 space-y-4">
              <span className="font-syne text-3xl font-extrabold tracking-widest text-[#E60000] block">
                {STUDIO_CONFIG.name}
              </span>
              <p className="text-xs font-syne font-semibold uppercase tracking-[0.2em] text-neutral-400">
                {STUDIO_CONFIG.tagline}
              </p>
              <p className="font-epilogue text-sm text-neutral-400 max-w-sm leading-relaxed">
                Estúdio de tatuagem focado em arte autoral, peças exclusivas e atendimento individualizado.
              </p>

              <div className="flex items-center gap-3 pt-2">
                <a
                  href={STUDIO_CONFIG.instagramUrl}
                  target="_blank"
                  rel="noopener noreferrer"
                  className="flex items-center gap-2 p-2.5 bg-[#121212] border border-[#262626] text-neutral-300 hover:text-white hover:border-[#E60000] hover:bg-[#E60000]/10 transition-colors"
                  aria-label="Instagram da Abarr Tattoo"
                >
                  <Instagram className="w-4 h-4 text-[#E60000]" />
                  <span className="text-xs font-epilogue">{STUDIO_CONFIG.instagramHandle}</span>
                </a>

                <a
                  href={STUDIO_CONFIG.whatsappUrl}
                  target="_blank"
                  rel="noopener noreferrer"
                  className="flex items-center gap-2 p-2.5 bg-[#121212] border border-[#262626] text-neutral-300 hover:text-white hover:border-[#E60000] hover:bg-[#E60000]/10 transition-colors"
                  aria-label="WhatsApp da Abarr Tattoo"
                >
                  <MessageCircle className="w-4 h-4 text-[#E60000]" />
                  <span className="text-xs font-epilogue">WhatsApp Direto</span>
                </a>
              </div>
            </div>

            <div className="md:col-span-3 space-y-4">
              <h4 className="font-syne text-xs uppercase font-bold tracking-widest text-neutral-400">
                Navegação
              </h4>
              <ul className="space-y-2.5 text-xs font-epilogue text-neutral-400">
                <li>
                  <a href="#portfolio" className="hover:text-white transition-colors">
                    Portfólio & Obras
                  </a>
                </li>
                <li>
                  <a href="#processo" className="hover:text-white transition-colors">
                    Do Esboço à Cicatrização
                  </a>
                </li>
                <li>
                  <a href="#orcamento" className="hover:text-white transition-colors">
                    Simulador de Orçamento
                  </a>
                </li>
                <li>
                  <a href="#duvidas" className="hover:text-white transition-colors">
                    Dúvidas Frequentes
                  </a>
                </li>
              </ul>
            </div>

            <div className="md:col-span-4 space-y-4">
              <h4 className="font-syne text-xs uppercase font-bold tracking-widest text-neutral-400">
                Localização & Atendimento
              </h4>
              <div className="space-y-3 text-xs font-epilogue text-neutral-300">
                <div className="flex items-start gap-3">
                  <MapPin className="w-4 h-4 text-[#E60000] shrink-0 mt-0.5" />
                  <span>{STUDIO_CONFIG.location}</span>
                </div>
                <div className="flex items-start gap-3">
                  <Phone className="w-4 h-4 text-[#E60000] shrink-0 mt-0.5" />
                  <a href={STUDIO_CONFIG.whatsappUrl} className="hover:text-white transition-colors">
                    {STUDIO_CONFIG.phoneFormatted}
                  </a>
                </div>
                <div className="flex items-start gap-3">
                  <Clock className="w-4 h-4 text-[#E60000] shrink-0 mt-0.5" />
                  <span className="text-neutral-400">{STUDIO_CONFIG.hours}</span>
                </div>
              </div>
            </div>
          </div>

          <div className="mt-14 pt-8 border-t border-[#262626] flex flex-col sm:flex-row items-center justify-between gap-4 text-xs font-epilogue text-neutral-500">
            <p>© 2026 {STUDIO_CONFIG.fullName}. Todos os direitos reservados.</p>
            <p className="text-[11px] text-neutral-500">
              Dark Premium · Tatuagens Autorais Exclusivas · Florianópolis/SC
            </p>
          </div>
        </div>
      </footer>
    </div>
  );
}
