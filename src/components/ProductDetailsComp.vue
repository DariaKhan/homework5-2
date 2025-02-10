<template>
  <div>
    <h2>Список продуктов</h2>
    <div v-for="product in products" :key="product.id">
      <h2>{{ product.id }} - {{ product.name }}</h2>
      <p>Цена в рублях: {{ product.price }} р.</p>
      <p>Цена в долларах: {{ formattedPrice(product.price) }}</p>
      <p v-if="product.available">В наличии</p>
      <p v-else>Нет в наличии</p>
    </div>
  </div>
</template>

<script>
export default {
  name: 'ProductDetailsComp',
  data () {
    return {
      products: [
        {
          id: 1,
          name: 'Рубашка',
          price: 1200,
          available: true
        },
        {
          id: 2,
          name: 'Брюки',
          price: 2100,
          available: false
        },
        {
          id: 3,
          name: 'Куртка',
          price: 3105,
          available: true
        }
      ],
      currencies: [
        {
          id: 1,
          name: 'USD',
          ratetoRub: 100
        },
        {
          id: 2,
          name: 'EUR',
          ratetoRub: 90
        },
        {
          id: 3,
          name: 'RUB',
          ratetoRub: 1
        }
      ]
    }
  },
  methods: {},
  computed: {
    formattedPrice () {
      return (price) => {
        return '$' + (price / 100).toFixed(2)
      }
    }
  },
  mounted () {}
}
</script>

<style scoped></style>

<!-- Часть 2. Задание Vue Вы разрабатываете приложение для интернет-магазина и у вас есть компонент Vue под названием "ProductDetails".
Компонент отображает детали о конкретном продукте, включая его название, цену и статус доступности.
Внутри компонента "ProductDetails" создайте свойство "product" с объектом, представляющим информацию о продукте. Объект должен иметь свойства "name" (название продукта), "price" (цена продукта) и "available" (флаг, указывающий на доступность продукта).
Используя вычисляемое свойство, назовите его "formattedPrice", которое будет возвращать форматированную цену продукта со знаком валюты. Например, если цена равна 99.99, вычисляемое свойство должно вернуть строку "$99.99".
В компоненте "ProductDetails" отобразите название продукта, его форматированную цену и статус доступности.
Если продукт доступен, отобразите текст "Available", в противном случае - "Out of stock".
 -->
