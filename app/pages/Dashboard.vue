<template>
  <div class="container mx-auto p-6 max-w-6xl">
    <div class="grid grid-cols-1 lg:grid-cols-2 gap-8">

      <!-- FORMULAIRE -->
      <div class="card bg-black shadow-xl border-2 border-orange ">
        <div class="card-body">
          <h2 class="card-title text-2xl mb-4">Ajouter un lieu</h2>

          <form @submit.prevent="handleSubmit">
            <!-- Nom du lieu -->
            <div class="form-control w-full mb-4">
              <label class="label">
                <span class="label-text">Nom du lieu</span>
              </label>
              <input v-model="formData.nom" type="text" placeholder="Ex: Le Café des Arts"
                class="input input-bordered w-full" required />
            </div>

            <!-- Images (URLs) -->
            <div class="form-control w-full mb-4">
              <label class="label">
                <span class="label-text">Images (URLs, séparées par des virgules)</span>
              </label>
              <textarea v-model="formData.images"
                placeholder="https://example.com/image1.jpg, https://example.com/image2.jpg"
                class="textarea textarea-bordered h-20"></textarea>
            </div>

            <!-- Adresse -->
            <div class="form-control w-full mb-4">
              <label class="label">
                <span class="label-text">Adresse</span>
              </label>
              <textarea v-model="formData.adresse" placeholder="rue Bayard, 31000..."
                class="textarea textarea-bordered h-24" required></textarea>
            </div>

            <!-- Horaires -->
            <div class="form-control w-full mb-4">
              <label class="label">
                <span class="label-text">Horaires d'ouverture</span>
              </label>
              <textarea v-model="formData.horaires" placeholder="Lun-Ven: 9h-18h&#10;Sam-Dim: 10h-16h"
                class="textarea textarea-bordered h-24" required></textarea>
            </div>

            <!-- Description -->
            <div class="form-control w-full mb-4">
              <label class="label">
                <span class="label-text">Description</span>
              </label>
              <textarea v-model="formData.description" placeholder="Décrivez le lieu..."
                class="textarea textarea-bordered h-32" required></textarea>
            </div>

            <!-- Réseaux sociaux -->
            <div class="divider">Réseaux sociaux</div>

            <div class="form-control w-full mb-3">
              <label class="label">
                <span class="label-text">Facebook</span>
              </label>
              <input v-model="formData.reseaux.facebook" type="url" placeholder="https://facebook.com/..."
                class="input input-bordered w-full input-sm" />
            </div>

            <div class="form-control w-full mb-3">
              <label class="label">
                <span class="label-text">Instagram</span>
              </label>
              <input v-model="formData.reseaux.instagram" type="url" placeholder="https://instagram.com/..."
                class="input input-bordered w-full input-sm" />
            </div>

            <div class="form-control w-full mb-3">
              <label class="label">
                <span class="label-text">Twitter/X</span>
              </label>
              <input v-model="formData.reseaux.twitter" type="url" placeholder="https://twitter.com/..."
                class="input input-bordered w-full input-sm" />
            </div>

            <div class="form-control w-full mb-4">
              <label class="label">
                <span class="label-text">Site web</span>
              </label>
              <input v-model="formData.reseaux.website" type="url" placeholder="https://example.com"
                class="input input-bordered w-full input-sm" />
            </div>

            <!-- Options friendly -->
            <div class="divider">Options</div>

            <div class="form-control mb-3">
              <label class="label cursor-pointer">
                <span class="label-text">Vegan Friendly 🌱</span>
                <input v-model="formData.veganFriendly" type="checkbox" class="checkbox checkbox-success" />
              </label>
            </div>

            <div class="form-control mb-3">
              <label class="label cursor-pointer">
                <span class="label-text">Handi Friendly ♿</span>
                <input v-model="formData.handiFriendly" type="checkbox" class="checkbox checkbox-info" />
              </label>
            </div>

            <div class="form-control mb-6">
              <label class="label cursor-pointer">
                <span class="label-text">Pet Friendly 🐾</span>
                <input v-model="formData.petFriendly" type="checkbox" class="checkbox checkbox-warning" />
              </label>
            </div>

            <button type="submit" class="btn border-2 border-orange w-full bg-black hover:bg-orange hover:text-white">
              Ajouter le lieu
            </button>
          </form>
        </div>
      </div>

      <!-- CARD D'AFFICHAGE -->
      <div v-if="lieu" class="card bg-black shadow-xl border-2 border-orange">
        <!-- Carousel d'images -->
        <figure v-if="lieu.imagesArray.length > 0" class="relative">
          <div class="carousel w-full h-64">
            <div v-for="(img, index) in lieu.imagesArray" :key="index" :id="`slide${index}`"
              class="carousel-item relative w-full">
              <img :src="img" class="w-full object-cover" :alt="`Image ${index + 1}`" />
            </div>
          </div>
        </figure>

        <div class="card-body">
          <!-- Nom du lieu -->
          <h2 class="card-title text-3xl text-title font-titan">{{ lieu.nom }}</h2>

          <!-- Badges friendly -->
          <div class="flex gap-2 flex-wrap my-2">
            <div v-if="lieu.veganFriendly" class="badge badge-success gap-2">
              🌱 Vegan Friendly
            </div>
            <div v-if="lieu.handiFriendly" class="badge badge-info gap-2">
              ♿ Handi Friendly
            </div>
            <div v-if="lieu.petFriendly" class="badge badge-warning gap-2">
              🐾 Pet Friendly
            </div>
          </div>
          <!-- Adresse -->
          <div class="mt-2">
            <h3 class="font-semibold text-lg mb-2">🏡 Adresse</h3>
            <p class=" text-sm">{{ lieu.adresse }}</p>
          </div>

          <!-- Horaires -->
          <div class="mt-2">
            <h3 class="font-semibold text-lg mb-2">🕐 Horaires</h3>
            <p class=" text-sm">{{ lieu.horaires }}</p>
          </div>

          <!-- Description -->
                    <div class="mt-2">
            <h3 class="font-semibold text-lg mb-2">🗒️ Description</h3>
            <p class=" text-sm">{{ lieu.description }}</p>
          </div>

          <!-- Réseaux sociaux -->
          <div v-if="hasReseaux" class="mt-4">
            <h3 class="font-semibold text-lg mb-2">📱 Nous suivre</h3>
            <div class="flex gap-3 flex-wrap">
              <a v-if="lieu.reseaux.facebook" :href="lieu.reseaux.facebook" target="_blank"
                class="btn btn-circle btn-sm btn-orange btn-outline text-orange">
                F
              </a>
              <a v-if="lieu.reseaux.instagram" :href="lieu.reseaux.instagram" target="_blank"
                class="btn btn-circle btn-sm btn-orange btn-outline text-orange">
                I
              </a>
              <a v-if="lieu.reseaux.twitter" :href="lieu.reseaux.twitter" target="_blank"
                class="btn btn-circle btn-sm btn-orange btn-outline text-orange">
                X
              </a>
              <a v-if="lieu.reseaux.website" :href="lieu.reseaux.website" target="_blank"
                class="btn btn-sm btn-orange btn-outline text-orange">
                🌐 Site web
              </a>
            </div>
          </div>
        </div>
      </div>

      <!-- Message si pas encore de lieu -->
      <div v-else class="card bg-black shadow-xl border-2 border-orange">
        <div class="card-body items-center text-center">
          <h2 class="card-title">Aucun lieu ajouté</h2>
          <p>Remplissez le formulaire pour voir la card s'afficher ici ! ✨</p>
        </div>
      </div>

    </div>
  </div>
</template>

<script setup>
import { ref, computed } from 'vue'

const formData = ref({
  nom: '',
  images: '',
  adresse: '',
  horaires: '',
  description: '',
  reseaux: {
    facebook: '',
    instagram: '',
    twitter: '',
    website: ''
  },
  veganFriendly: false,
  handiFriendly: false,
  petFriendly: false
})

const lieu = ref(null)

const handleSubmit = () => {
  // Traitement des images (conversion string vers array)
  const imagesArray = formData.value.images
    ? formData.value.images.split(',').map(url => url.trim()).filter(url => url)
    : []

  // Création de l'objet lieu
  lieu.value = {
    ...formData.value,
    imagesArray
  }

  // Optionnel : réinitialiser le formulaire
  // resetForm()
}

const hasReseaux = computed(() => {
  if (!lieu.value) return false
  const r = lieu.value.reseaux
  return r.facebook || r.instagram || r.twitter || r.website
})

const resetForm = () => {
  formData.value = {
    nom: '',
    images: '',
    adresse: '',
    horaires: '',
    description: '',
    reseaux: {
      facebook: '',
      instagram: '',
      twitter: '',
      website: ''
    },
    veganFriendly: false,
    handiFriendly: false,
    petFriendly: false
  }
}
</script>

<style scoped>
/* Styles additionnels si nécessaire */
</style>