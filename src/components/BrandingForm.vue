<template>
  <div class="text-center">
    <div class="max-w-4xl mx-auto bg-white p-6 rounded-lg shadow-md">
      <h1 class="text-2xl font-semibold mb-6">FICHE CLIENT</h1>
      <form ref='form' @submit.prevent="sendEmail">
        <div class="grid grid-cols-2 gap-6 mb-6">
          <div>
            <label for="company" class="block font-medium text-gray-700">Nom de l’entreprise</label>
            <input type="text" id="company" name="company" v-model="formData.company"
              class="mt-1 block w-full px-3 py-2 border border-gray-300 rounded-md shadow-sm focus:outline-none focus:ring-indigo-500 focus:border-indigo-500" />
          </div>
          <div>
            <label for="requestDate" class="block font-medium text-gray-700">Date de la demande</label>
            <input type="date" id="requestDate" name="requestDate" v-model="formData.requestDate"
              class="mt-1 block w-full px-3 py-2 border border-gray-300 rounded-md shadow-sm focus:outline-none focus:ring-indigo-500 focus:border-indigo-500" />
          </div>
        </div>

        <div class="grid grid-cols-2 gap-6 mb-6">
          <div class="mb-6">
            <label for="requestor" class="block font-medium text-gray-700">Nom et coordonnées du demandeur</label>
            <input type="text" id="requestor" name="requestor" v-model="formData.requestor"
              class="mt-1 block w-full px-3 py-2 border border-gray-300 rounded-md shadow-sm focus:outline-none focus:ring-indigo-500 focus:border-indigo-500" />
          </div>
          <div>
            <label for="desiredDeadline" class="block font-medium text-gray-700">Délai souhaité</label>
            <input type="date" id="desiredDeadline" name="desiredDeadline" v-model="formData.desiredDeadline"
              class="mt-1 block w-full px-3 py-2 border border-gray-300 rounded-md shadow-sm focus:outline-none focus:ring-indigo-500 focus:border-indigo-500" />
          </div>
        </div>

        <div class="mb-6">
          <label for="contactGMB" class="block font-medium text-gray-700">Contact GMB</label>
          <input type="text" id="contactGMB" name="contactGMB" v-model="formData.contactGMB"
            class="mt-1 block w-full px-3 py-2 border border-gray-300 rounded-md shadow-sm focus:outline-none focus:ring-indigo-500 focus:border-indigo-500" />
        </div>

        <div class="mb-6">
          <label for="address" class="block font-medium text-gray-700">Adresse postale</label>
          <input type="text" id="address" name="address" v-model="formData.address"
            class="mt-1 block w-full px-3 py-2 border border-gray-300 rounded-md shadow-sm focus:outline-none focus:ring-indigo-500 focus:border-indigo-500" />
        </div>

        <div class="grid grid-cols-2 gap-6 mb-6">
          <div>
            <label for="postalCode" class="block font-medium text-gray-700">Code postal</label>
            <input type="text" id="postalCode" name="postalCode" v-model="formData.postalCode"
              class="mt-1 block w-full px-3 py-2 border border-gray-300 rounded-md shadow-sm focus:outline-none focus:ring-indigo-500 focus:border-indigo-500" />
          </div>
          <div>
            <label for="city" class="block font-medium text-gray-700">Ville</label>
            <input type="text" id="city" name="city" v-model="formData.city"
              class="mt-1 block w-full px-3 py-2 border border-gray-300 rounded-md shadow-sm focus:outline-none focus:ring-indigo-500 focus:border-indigo-500" />
          </div>
        </div>



        <h2 class="text-xl font-semibold mb-4">BESOIN :</h2>

        <div class="grid grid-cols-2 gap-6 mb-6">
          <div>
            <label for="productCode" class="block font-medium text-gray-700">Code produit</label>
            <input type="text" id="productCode" name="productCode" v-model="formData.productCode"
              class="mt-1 block w-full px-3 py-2 border border-gray-300 rounded-md shadow-sm focus:outline-none focus:ring-indigo-500 focus:border-indigo-500" />
          </div>
          <div>
            <label for="quantity" class="block font-medium text-gray-700">Quantité</label>
            <input type="number" id="quantity" name="quantity" v-model="formData.quantity"
              class="mt-1 block w-full px-3 py-2 border border-gray-300 rounded-md shadow-sm focus:outline-none focus:ring-indigo-500 focus:border-indigo-500" />
          </div>
        </div>

        <div class="mb-6">
          <label for="requestDetail" class="block font-medium text-gray-700">Détail de la demande</label>
          <textarea id="requestDetail" name="requestDetail" v-model="formData.details"
            class="mt-1 block w-full px-3 py-2 border border-gray-300 rounded-md shadow-sm focus:outline-none focus:ring-indigo-500 focus:border-indigo-500"
            rows="4"></textarea>
        </div>

        <div class="mb-6">
          <div class="flex justify-between">
            <label class="block font-medium text-gray-700">Conditionnement à prévoir</label>
            <div class="flex items-center">
              <input type="radio" id="conditionYes" name="conditionnement" value="oui" class="mr-2"
                v-model="formData.conditionnement" />
              <label for="conditionYes" class="mr-4">OUI</label>
              <input type="radio" id="conditionNo" name="conditionnement" value="non" class="mr-2"
                v-model="formData.conditionnement" />
              <label for="conditionNo">NON</label>
            </div>
          </div>
          <div class="mt-2">
            <label for="conditionDetail" class="block font-medium text-gray-700">Si oui, quel conditionnement:</label>
            <input type="text" id="conditionDetail" name="conditionDetail" v-model="formData.conditionDetail"
              class="mt-1 block w-full px-3 py-2 border border-gray-300 rounded-md shadow-sm focus:outline-none focus:ring-indigo-500 focus:border-indigo-500" />
          </div>
        </div>

        <div class="mb-6">
          <div class="flex justify-between">

            <label class="block font-medium text-gray-700">Etiquetage du produit</label>
            <div class="flex items-center">
              <input type="radio" id="labelYes" name="label" value="oui" class="mr-2" v-model="formData.label" />
              <label for="labelYes" class="mr-4">OUI</label>
              <input type="radio" id="labelNo" name="label" value="non" class="mr-2" v-model="formData.label" />
              <label for="labelNo">NON</label>
            </div>
          </div>
          <div class="mt-2">
            <label for="labelDetail" class="block font-medium text-gray-700">Si oui, quelles mentions ?</label>
            <input type="text" id="labelDetail" name="labelDetail" v-model="formData.labelDetail"
              class="mt-1 block w-full px-3 py-2 border border-gray-300 rounded-md shadow-sm focus:outline-none focus:ring-indigo-500 focus:border-indigo-500" />
          </div>
        </div>

        <h2 class="text-xl font-semibold mb-4">CHARTE GRAPHIQUE :</h2>

        <div class="mb-6">
          <div class="flex justify-between">
            <p class="text-gray-700">Votre logo sera fourni au format :</p>
            <div class="flex items-center">
              <input type="checkbox" id="fileAI" name="fileAI" class="mr-2" v-model="formData.fileFormat" />
              <label for="fileAI" class="mr-4">AI</label>
              <input type="checkbox" id="fileEPS" name="fileEPS" class="mr-2" v-model="formData.fileFormat" />
              <label for="fileEPS">EPS</label>
            </div>
          </div>
        </div>

        <div class="mb-6">
          <label for="logoSize" class="block font-medium text-gray-700">Taille du logo souhaité sur le produit</label>
          <input type="text" id="logoSize" name="logoSize" v-model="formData.logoSize"
            class="mt-1 block w-full px-3 py-2 border border-gray-300 rounded-md shadow-sm focus:outline-none focus:ring-indigo-500 focus:border-indigo-500" />
        </div>

        <div class="mb-6">
          <label for="positioning" class="block font-medium text-gray-700">Positionnement</label>
          <input type="text" id="positioning" name="positioning" v-model="formData.positioning"
            class="mt-1 block w-full px-3 py-2 border border-gray-300 rounded-md shadow-sm focus:outline-none focus:ring-indigo-500 focus:border-indigo-500" />
        </div>

        <div class="mb-6">
          <label for="customizationType" class="block font-medium text-gray-700">Type de personnalisation
            souhaitée</label>
          <input type="text" id="customizationType" name="customizationType" v-model="formData.customizationType"
            class="mt-1 block w-full px-3 py-2 border border-gray-300 rounded-md shadow-sm focus:outline-none focus:ring-indigo-500 focus:border-indigo-500" />
        </div>

        <div class="mb-6">
          <label class="block font-medium text-gray-700">Couleur (indiquer le/les numéro(s) de pantone)</label>
          <input type="text" id="pantoneColor" name="pantoneColor" v-model="formData.pantoneColor"
            class="mt-1 block w-full px-3 py-2 border border-gray-300 rounded-md shadow-sm focus:outline-none focus:ring-indigo-500 focus:border-indigo-500" />
        </div>

        <div class="mb-6">
          <label class="block font-medium text-gray-700">Condition d’utilisation</label>
          <div class="flex justify-between">
            <label class="block font-medium text-gray-700">Garantie lave-vaisselle ?</label>
            <div class="flex items-center">
              <input type="radio" id="dishwasherYes" name="dishwasher" value="oui" class="mr-2"
                v-model="formData.dishwasher" />
              <label for="dishwasherYes" class="mr-4">OUI</label>
              <input type="radio" id="dishwasherNo" name="dishwasher" value="non" class="mr-2"
                v-model="formData.dishwasher" />
              <label for="dishwasherNo">NON</label>
            </div>
          </div>
          <div class="mt-2">
            <label for="otherCondition" class="block font-medium text-gray-700">Autre :</label>
            <input type="text" id="otherCondition" name="otherCondition" v-model="formData.otherCondition"
              class="mt-1 block w-full px-3 py-2 border border-gray-300 rounded-md shadow-sm focus:outline-none focus:ring-indigo-500 focus:border-indigo-500" />
          </div>
        </div>

        <div class="mb-6">
          <div class="flex justify-between">
            <label class="block font-medium text-gray-700">Gravure</label>
            <div class="flex items-center">
              <input type="radio" id="engraveYes" name="engrave" value="oui" class="mr-2" v-model="formData.engrave" />
              <label for="engraveYes" class="mr-4">OUI</label>
              <input type="radio" id="engraveNo" name="engrave" value="non" class="mr-2" v-model="formData.engrave" />
              <label for="engraveNo">NON</label>
            </div>
          </div>
        </div>

        <div class="flex justify-center mt-8">
          <button type="submit"
            class="px-6 py-3 bg-indigo-600 text-white rounded-md shadow-md hover:bg-indigo-700 focus:outline-none focus:ring-2 focus:ring-indigo-500">Soumettre</button>
        </div>
      </form>
    </div>
  </div>
</template>

<script>
import emailjs from '@emailjs/browser';

export default {
  name: 'BrandingForm',
  data() {
    return {
      formData: {
        company: '',
        requestDate: '',
        address: '',
        desiredDeadline: '',
        requestor: '',
        contactGMB: '',
        productCode: '',
        quantity: '',
        requestDetail: '',
        conditionnement: '',
        label: '',
        logoSize: '',
        pantoneColor: '',
        dishwasher: '',
      }
    }
  },
  methods: {
    sendEmail() {
      emailjs.sendForm(
        process.env.VUE_APP_EMAILJS_SERVICE_ID, 
        process.env.VUE_APP_EMAILJS_TEMPLATE_ID, 
        this.$refs.form, {
          publicKey: process.env.VUE_APP_EMAILJS_PUBLIC_KEY,
        })
        .then((response) => {
          console.log('SUCCESS', response);
          alert("Votre demande a été envoyée avec succès !")
        }, (error) => {
          console.log('FAILED', error);
          alert("Une erreur est survenue. Essayez à nouveau.")
        });
    }
  }
}
</script>