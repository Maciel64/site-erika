<template>
  <div class="font-sans">
    <header class="fixed top-0 left-0 right-0 z-50 bg-white/80 backdrop-blur-md shadow-sm">
      <div class="container mx-auto px-4 py-3">
        <nav class="flex items-center justify-between">
          <div class="flex items-center gap-2">
            <UIcon name="leaf" class="text-emerald-500 text-2xl" />
            <h1 class="text-xl font-bold text-emerald-700">Erika Medeiros</h1>
          </div>
          <div class="hidden md:flex gap-6">
            <a v-for="(item, i) in navItems" :key="i" 
               :href="item.href" 
               class="text-gray-600 hover:text-emerald-500 transition-colors">
              {{ item.label }}
            </a>
          </div>
          <UButton 
            color="emerald" 
            variant="soft" 
            to="#contato" 
            class="hidden md:block">
            Agendar Consulta
          </UButton>
          <UButton 
            icon="i-heroicons-bars-3" 
            color="gray" 
            variant="ghost" 
            class="md:hidden" 
            @click="isMenuOpen = !isMenuOpen" />
        </nav>
      </div>
    </header>

    <UModal v-model="isMenuOpen" class="md:hidden">
      <div class="p-4 flex flex-col gap-4">
        <a v-for="(item, i) in navItems" :key="i" 
           :href="item.href" 
           class="text-gray-600 hover:text-emerald-500 transition-colors py-2 text-lg"
           @click="isMenuOpen = false">
          {{ item.label }}
        </a>
        <UButton 
          color="emerald" 
          to="#contato" 
          block 
          @click="isMenuOpen = false">
          Agendar Consulta
        </UButton>
      </div>
    </UModal>

    <!-- Hero Section -->
    <section id="inicio" class="min-h-screen pt-24 pb-16 flex items-center">
      <div class="container mx-auto px-4">
        <div class="grid md:grid-cols-2 gap-8 items-center">
          <div 
            v-motion
            :initial="{ opacity: 0, y: 100 }"
            :enter="{ opacity: 1, y: 0, transition: { delay: 200 } }">
            <h1 class="text-4xl md:text-5xl font-bold text-gray-800 mb-4">
              Transforme sua saúde com nutrição personalizada
            </h1>
            <p class="text-lg text-gray-600 mb-6">
              Olá, sou Dra. Erika Medeiros, nutricionista formada pela Universidade Federal do Rio Grande do Norte. Vamos juntos construir hábitos alimentares que transformarão sua vida.
            </p>
            <div class="flex flex-wrap gap-4">
              <UButton 
                color="emerald" 
                size="lg" 
                to="#contato">
                Agendar Consulta
              </UButton>
              <UButton 
                color="gray" 
                variant="soft" 
                size="lg" 
                to="#sobre">
                Saiba Mais
              </UButton>
            </div>
          </div>
          <div 
            class="relative"
            v-motion
            :initial="{ opacity: 0, x: 100 }"
            :enter="{ opacity: 1, x: 0, transition: { delay: 400 } }">
            <img 
              src="/public/erika2.jpeg" 
              alt="Nutricionista" 
              class="rounded-lg shadow-xl w-full max-w-md mx-auto" />
            <div class="absolute -bottom-6 -right-6 bg-emerald-50 p-4 rounded-lg shadow-lg hidden md:block">
              <div class="flex items-center gap-3">
                <UIcon name="i-heroicons-star" class="text-yellow-400 text-xl" />
                <div>
                  <p class="font-bold text-gray-800">+500 clientes satisfeitos</p>
                  <p class="text-sm text-gray-600">Resultados comprovados</p>
                </div>
              </div>
            </div>
          </div>
        </div>
      </div>
    </section>

    <section id="sobre" class="py-16 bg-emerald-50">
      <div class="container mx-auto px-4">
        <div 
          class="text-center mb-12"
          v-motion
          :initial="{ opacity: 0, y: 50 }"
          :visible="{ opacity: 1, y: 0 }">
          <h2 class="text-3xl font-bold text-gray-800 mb-2">Sobre Mim</h2>
          <div class="w-20 h-1 bg-emerald-500 mx-auto"></div>
        </div>
        
        <div class="grid md:grid-cols-2 gap-8 items-center">
          <div 
            class="order-2 md:order-1"
            v-motion
            :initial="{ opacity: 0, x: -50 }"
            :visible="{ opacity: 1, x: 0 }">
            <h3 class="text-2xl font-bold text-gray-800 mb-4">Dra. Erika Medeiros</h3>
            <p class="text-gray-600 mb-4">
              Nutricionista formada pela Universidade Federal com mais de 10 anos de experiência clínica. Especialista em nutrição funcional e comportamental.
            </p>
            <p class="text-gray-600 mb-4">
              Minha abordagem é personalizada e focada em resultados sustentáveis. Acredito que a alimentação deve ser prazerosa e adaptada ao estilo de vida de cada pessoa.
            </p>
            <div class="grid grid-cols-2 gap-4 mt-6">
              <div class="bg-white p-4 rounded-lg shadow-sm">
                <UIcon name="i-heroicons-academic-cap" class="text-emerald-500 text-2xl mb-2" />
                <h4 class="font-bold text-gray-800">Formação</h4>
                <p class="text-sm text-gray-600">Especialista em Nutrição Funcional</p>
              </div>
              <div class="bg-white p-4 rounded-lg shadow-sm">
                <UIcon name="i-heroicons-briefcase" class="text-emerald-500 text-2xl mb-2" />
                <h4 class="font-bold text-gray-800">Experiência</h4>
                <p class="text-sm text-gray-600">+10 anos de atuação clínica</p>
              </div>
            </div>
          </div>
          <div 
            class="order-1 md:order-2"
            v-motion
            :initial="{ opacity: 0, x: 50 }"
            :visible="{ opacity: 1, x: 0 }">
            <img 
              src="/public/erika.jpeg" 
              alt="Dra. Erika Medeiros" 
              class="rounded-lg shadow-xl w-full max-w-md mx-auto" />
          </div>
        </div>
      </div>
    </section>

    <section id="depoimentos" class="py-16">
      <div class="container mx-auto px-4">
        <div 
          class="text-center mb-12"
          v-motion
          :initial="{ opacity: 0, y: 50 }"
          :visible="{ opacity: 1, y: 0 }">
          <h2 class="text-3xl font-bold text-gray-800 mb-2">Depoimentos</h2>
          <div class="w-20 h-1 bg-emerald-500 mx-auto mb-4"></div>
          <p class="text-gray-600 max-w-2xl mx-auto">
            Veja o que meus clientes têm a dizer sobre os resultados alcançados com meus programas nutricionais.
          </p>
        </div>
        
        <div class="grid md:grid-cols-3 gap-6">
          <div 
            v-for="(testimonial, i) in testimonials" 
            :key="i"
            v-motion
            :initial="{ opacity: 0, y: 50 }"
            :visible="{ opacity: 1, y: 0, transition: { delay: i * 200 } }"
            class="bg-white p-6 rounded-lg shadow-md">
            <div class="flex items-center gap-2 mb-4">
              <UIcon name="i-heroicons-star" class="text-yellow-400" v-for="star in 5" :key="star" />
            </div>
            <p class="text-gray-600 mb-4 italic">
              "{{ testimonial.text }}"
            </p>
            <div class="flex items-center gap-3">
              <img 
                :src="`&text=${testimonial.name.charAt(0)}`" 
                :alt="testimonial.name" 
                class="w-12 h-12 rounded-full object-cover" />
              <div>
                <h4 class="font-bold text-gray-800">{{ testimonial.name }}</h4>
                <p class="text-sm text-gray-500">{{ testimonial.result }}</p>
              </div>
            </div>
          </div>
        </div>
      </div>
    </section>

    <section id="planos" class="py-16 bg-emerald-50">
      <div class="container mx-auto px-4">
        <div 
          class="text-center mb-12"
          v-motion
          :initial="{ opacity: 0, y: 50 }"
          :visible="{ opacity: 1, y: 0 }">
          <h2 class="text-3xl font-bold text-gray-800 mb-2">Planos Nutricionais</h2>
          <div class="w-20 h-1 bg-emerald-500 mx-auto mb-4"></div>
          <p class="text-gray-600 max-w-2xl mx-auto">
            Escolha o plano que melhor se adapta às suas necessidades e objetivos.
          </p>
        </div>
        
        <div class="grid md:grid-cols-3 gap-6">
          <div 
            v-for="(plan, i) in plans" 
            :key="i"
            v-motion
            :initial="{ opacity: 0, y: 50 }"
            :visible="{ opacity: 1, y: 0, transition: { delay: i * 200 } }"
            class="bg-white rounded-lg shadow-md overflow-hidden">
            <div class="p-6" :class="i === 1 ? 'bg-emerald-500' : 'bg-gray-100'">
              <h3 class="text-xl font-bold mb-2" :class="i === 1 ? 'text-white' : 'text-gray-800'">
                {{ plan.name }}
              </h3>
              <div class="flex items-end gap-1">
                <span class="text-3xl font-bold" :class="i === 1 ? 'text-white' : 'text-gray-800'">
                  R$ {{ plan.price }}
                </span>
                <span :class="i === 1 ? 'text-white/80' : 'text-gray-500'">
                  {{ plan.period }}
                </span>
              </div>
            </div>
            <div class="p-6">
              <ul class="space-y-3 mb-6">
                <li v-for="(feature, j) in plan.features" :key="j" class="flex items-start gap-2">
                  <UIcon name="i-heroicons-check-circle" class="text-emerald-500 mt-1 flex-shrink-0" />
                  <span class="text-gray-600">{{ feature }}</span>
                </li>
              </ul>
              <UButton 
                :color="i === 1 ? 'emerald' : 'gray'" 
                :variant="i === 1 ? 'solid' : 'outline'" 
                block 
                to="#contato">
                Escolher Plano
              </UButton>
            </div>
          </div>
        </div>
      </div>
    </section>

    <section id="contato" class="py-16">
      <div class="container mx-auto px-4">
        <div 
          class="text-center mb-12"
          v-motion
          :initial="{ opacity: 0, y: 50 }"
          :visible="{ opacity: 1, y: 0 }">
          <h2 class="text-3xl font-bold text-gray-800 mb-2">Entre em Contato</h2>
          <div class="w-20 h-1 bg-emerald-500 mx-auto mb-4"></div>
          <p class="text-gray-600 max-w-2xl mx-auto">
            Estou pronta para ajudar você a alcançar seus objetivos de saúde e bem-estar.
          </p>
        </div>
        
        <div class="grid md:grid-cols-2 gap-8">
          <div 
            v-motion
            :initial="{ opacity: 0, x: -50 }"
            :visible="{ opacity: 1, x: 0 }">
            <div class="bg-white p-6 rounded-lg shadow-md">
              <h3 class="text-xl font-bold text-gray-800 mb-4">Informações de Contato</h3>
              
              <div class="space-y-4">
                <div class="flex items-start gap-3">
                  <UIcon name="i-heroicons-map-pin" class="text-emerald-500 text-xl flex-shrink-0 mt-1" />
                  <div>
                    <h4 class="font-bold text-gray-800">Endereço</h4>
                    <p class="text-gray-600">Av. Paulista, 1000 - Bela Vista, São Paulo - SP</p>
                  </div>
                </div>
                
                <div class="flex items-start gap-3">
                  <UIcon name="i-heroicons-phone" class="text-emerald-500 text-xl flex-shrink-0 mt-1" />
                  <div>
                    <h4 class="font-bold text-gray-800">Telefone</h4>
                    <p class="text-gray-600">(11) 99999-9999</p>
                  </div>
                </div>
                
                <div class="flex items-start gap-3">
                  <UIcon name="i-heroicons-envelope" class="text-emerald-500 text-xl flex-shrink-0 mt-1" />
                  <div>
                    <h4 class="font-bold text-gray-800">Email</h4>
                    <p class="text-gray-600">contato@erikamedeiros.com.br</p>
                  </div>
                </div>
                
                <div class="flex items-start gap-3">
                  <UIcon name="i-heroicons-clock" class="text-emerald-500 text-xl flex-shrink-0 mt-1" />
                  <div>
                    <h4 class="font-bold text-gray-800">Horário de Atendimento</h4>
                    <p class="text-gray-600">Segunda a Sexta: 8h às 18h</p>
                  </div>
                </div>
              </div>
              
              <div class="mt-6">
                <UButton 
                  color="emerald" 
                  icon="i-heroicons-chat-bubble-left-right" 
                  size="lg" 
                  class="w-full"
                  :to="whatsappLink">
                  Falar pelo WhatsApp
                </UButton>
              </div>
            </div>
          </div>
          
          <div 
            v-motion
            :initial="{ opacity: 0, x: 50 }"
            :visible="{ opacity: 1, x: 0 }">
            <div class="bg-white p-6 rounded-lg shadow-md">
              <h3 class="text-xl font-bold text-gray-800 mb-4">Envie uma Mensagem</h3>
              
              <form @submit.prevent="submitForm">
                <div class="space-y-4">
                  <UFormGroup label="Nome Completo">
                    <UInput v-model="form.name" placeholder="Seu nome completo" />
                  </UFormGroup>
                  
                  <UFormGroup label="Email">
                    <UInput v-model="form.email" type="email" placeholder="seu.email@exemplo.com" />
                  </UFormGroup>
                  
                  <UFormGroup label="Telefone">
                    <UInput v-model="form.phone" placeholder="(00) 00000-0000" />
                  </UFormGroup>
                  
                  <UFormGroup label="Mensagem">
                    <UTextarea v-model="form.message" placeholder="Como posso ajudar você?" rows="4" />
                  </UFormGroup>
                  
                  <UButton type="submit" color="emerald" block :loading="form.loading">
                    Enviar Mensagem
                  </UButton>
                </div>
              </form>
            </div>
          </div>
        </div>
      </div>
    </section>

    <footer class="bg-gray-800 text-white py-8">
      <div class="container mx-auto px-4">
        <div class="grid md:grid-cols-3 gap-8">
          <div>
            <div class="flex items-center gap-2 mb-4">
              <UIcon name="leaf" class="text-emerald-400 text-2xl" />
              <h3 class="text-xl font-bold">Erika Medeiros</h3>
            </div>
            <p class="text-gray-400">
              Transformando vidas através da nutrição personalizada e consciente.
            </p>
          </div>
          
          <div>
            <h4 class="text-lg font-bold mb-4">Links Rápidos</h4>
            <ul class="space-y-2">
              <li v-for="(item, i) in navItems" :key="i">
                <a :href="item.href" class="text-gray-400 hover:text-emerald-400 transition-colors">
                  {{ item.label }}
                </a>
              </li>
            </ul>
          </div>
          
          <div>
            <h4 class="text-lg font-bold mb-4">Redes Sociais</h4>
            <div class="flex gap-4">
              <a href="#" class="text-gray-400 hover:text-emerald-400 transition-colors">
                <UIcon name="i-heroicons-globe-alt" class="text-2xl" />
              </a>
              <a href="#" class="text-gray-400 hover:text-emerald-400 transition-colors">
                <UIcon name="i-heroicons-chat-bubble-oval-left" class="text-2xl" />
              </a>
              <a href="#" class="text-gray-400 hover:text-emerald-400 transition-colors">
                <UIcon name="i-heroicons-photo" class="text-2xl" />
              </a>
            </div>
          </div>
        </div>
        
        <div class="border-t border-gray-700 mt-8 pt-6 text-center text-gray-400">
          <p>&copy; {{ new Date().getFullYear() }} Dra. Erika Medeiros. Todos os direitos reservados.</p>
        </div>
      </div>
    </footer>
  </div>
</template>

<script setup>
import { ref, computed } from 'vue'

const isMenuOpen = ref(false)

const navItems = [
  { label: 'Início', href: '#inicio' },
  { label: 'Sobre', href: '#sobre' },
  { label: 'Depoimentos', href: '#depoimentos' },
  { label: 'Planos', href: '#planos' },
  { label: 'Contato', href: '#contato' }
]

const testimonials = [
  {
    name: 'Mariana Santos',
    text: 'Perdi 15kg em 6 meses com o acompanhamento da Dra. Ana. O melhor é que aprendi a me alimentar de forma saudável sem passar fome!',
    result: 'Perdeu 15kg em 6 meses'
  },
  {
    name: 'Carlos Oliveira',
    text: 'Depois de anos lutando contra a obesidade, finalmente encontrei uma abordagem que funciona. Já são 20kg a menos e muita disposição!',
    result: 'Perdeu 20kg em 8 meses'
  },
  {
    name: 'Juliana Costa',
    text: 'O plano alimentar se encaixou perfeitamente na minha rotina. Consegui melhorar minha saúde digestiva e ainda perdi 8kg no processo.',
    result: 'Melhorou saúde digestiva'
  }
]

// Planos
const plans = [
  {
    name: 'Plano Básico',
    price: '297',
    period: '/mês',
    features: [
      'Consulta inicial detalhada',
      'Plano alimentar personalizado',
      'Ajustes mensais',
      '1 consulta de acompanhamento',
      'Suporte por email'
    ]
  },
  {
    name: 'Plano Premium',
    price: '497',
    period: '/mês',
    features: [
      'Consulta inicial detalhada',
      'Plano alimentar personalizado',
      'Ajustes quinzenais',
      '2 consultas de acompanhamento',
      'Suporte por WhatsApp',
      'Receitas exclusivas',
      'Análise de exames laboratoriais'
    ]
  },
  {
    name: 'Plano Família',
    price: '797',
    period: '/mês',
    features: [
      'Atendimento para até 4 pessoas',
      'Planos alimentares personalizados',
      'Ajustes mensais',
      '1 consulta de acompanhamento por pessoa',
      'Suporte por WhatsApp',
      'Receitas exclusivas',
      'Orientações para refeições em família'
    ]
  }
]

const form = ref({
  name: '',
  email: '',
  phone: '',
  message: '',
  loading: false
})

const whatsappLink = computed(() => {
  const phone = '5511999999999' // Substitua pelo número real (com código do país)
  const message = encodeURIComponent('Olá! Gostaria de agendar uma consulta.')
  return `https://wa.me/${phone}?text=${message}`
})


const submitForm = () => {
  form.value.loading = true
  
  // Simulação de envio
  setTimeout(() => {
    form.value.loading = false
    alert('Mensagem enviada com sucesso! Entraremos em contato em breve.')
    
    // Limpar formulário
    form.value.name = ''
    form.value.email = ''
    form.value.phone = ''
    form.value.message = ''
  }, 1500)
}
</script>

<style>
html {
  scroll-behavior: smooth;
}

body {
  background-color: #fff;
  color: #333;
}
</style>