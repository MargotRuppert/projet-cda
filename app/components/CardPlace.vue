<template>
    <h1 class="text-4xl font-titan text-center text-title m-[20px] mt-6">Ajout d'un lieu</h1>
    <div class="flex justify-center">
        <fieldset class="fieldset bg-black rounded-box min-w-md border border-3 border-orange p-4 m-4 text-base">

            <label class="label text-white">Nom du lieu</label>
            <input type="text" class="input bg-white text-black outline-2 outline-orange focus:outline-orange"
                placeholder="Nom du lieu" v-model="placeName"/>

            <label class="label text-white">Adresse</label>
            <input type="text" class="input bg-white text-black outline-2 outline-orange focus:outline-black"
                placeholder="Adresse complète" v-model="placeAddress"/>

            <label class="label text-white">Images</label>
            <input type="file" class="file-input file-input-warning outline outline-orange bg-white text-black"/>

            <span>Description</span>
            <textarea class="textarea h-24 bg-white outline-2 outline-orange text-black"
                placeholder="Description" v-model="placeBio"></textarea>

            <span>Horaires</span>
            <textarea class="textarea h-24 bg-white outline-2 outline-orange text-black"
                placeholder="Horaires" v-model="placeOpening"></textarea>

            <!-- social medias -->
            <label class="label text-white">Réseau social 1 </label>
            <input type="text" class="input bg-white text-black outline-2 outline-orange focus:outline-orange"
                placeholder="Nom du réseau" />

            <label class="label text-white">Réseau social 2 </label>
            <input type="text" class="input bg-white text-black outline-2 outline-orange focus:outline-orange"
                placeholder="Nom du réseau" />

            <label class="label text-white">Réseau social 3 </label>
            <input type="text" class="input bg-white text-black outline-2 outline-orange focus:outline-orange"
                placeholder="Nom du réseau" />

            <!-- Checkboxes for inclusivity -->
            <div class="flex flex-col mt-3">
                <label class="label cursor-pointer mb-2">
                    <input type="checkbox" class="checkbox checkbox-warning" />
                    <span class="text-white">🌱 Vegan-friendly</span>
                </label>

                <label class="label cursor-pointer mb-2">
                    <input type="checkbox" class="checkbox checkbox-warning" />
                    <span class="text-white">♿ Handi-friendly</span>
                </label>

                <label class="label cursor-pointer mb-2">
                    <input type="checkbox" class="checkbox checkbox-warning" />
                    <span class="text-white">🐶 Pet-friendly</span>
                </label>

                <label class="label cursor-pointer mb-2">
                    <input type="checkbox" class="checkbox checkbox-warning" />
                    <span class="text-white">👶 Kid-friendly</span>
                </label>

                <label class="label cursor-pointer mb-2">
                    <input type="checkbox" class="checkbox checkbox-warning" />
                    <span class="text-white">🌍 Éco-responsable</span>
                </label>
            </div>
            <!-- adding button -->
            <button
                class="btn outline outline-orange text-orange bg-black mt-2 hover:bg-orange hover:text-white">Ajouter</button>
        </fieldset>
    </div>

</template>

<script setup>

</script>
