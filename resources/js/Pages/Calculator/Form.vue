<script setup lang="ts">
    import { SidebarProvider, SidebarTrigger } from "@/components/ui/sidebar";
    import { ToggleGroup, ToggleGroupItem } from '@/components/ui/toggle-group'
    import { Bold, Italic, Underline } from 'lucide-vue-next'

    import AppSidebar from "@/components/AppSidebar.vue";
    import { ref } from 'vue'
    const currency = ref('EUR')

    import {
    Card,
    CardContent,
    CardDescription,
    CardFooter,
    CardHeader,
    CardTitle,
    } from '@/components/ui/card'

</script>


<template>
<div class="p-6">
  <Card class="w-full lg:w-[600px] p-6 rounded-xl shadow-md space-y-4">
    <h1 class="text-2xl font-bold text-center">Currency Conversion</h1>

    <!-- Toggle for EUR / RON -->
    <div class="flex justify-center">
      <ToggleGroup
        type="single"
        v-model="currency"
        class="inline-flex bg-white rounded-full border overflow-hidden shadow"
      >
        <ToggleGroupItem
          value="EUR"
          class="px-6 py-2 text-sm font-medium focus:outline-none transition-colors duration-200"
          :class="
            currency === 'EUR'
              ? 'bg-blue-900 text-white'
              : 'bg-white text-gray-500'
          "
        >
          EUR
        </ToggleGroupItem>
        <ToggleGroupItem
          value="RON"
          class="px-6 py-2 text-sm font-medium focus:outline-none transition-colors duration-200"
          :class="
            currency === 'RON'
              ? 'bg-blue-900 text-white'
              : 'bg-white text-gray-500'
          "
        >
          RON
        </ToggleGroupItem>
      </ToggleGroup>
    </div>

    <!-- Exchange rate -->
    <div
      class="flex justify-between items-center text-sm font-semibold text-gray-700"
    >
      <span>Curs 8 April</span>
      <span>1 EUR = 4.9774 RON</span>
      <button class="text-gray-500 hover:text-gray-800">
        <svg
          class="w-5 h-5"
          fill="none"
          stroke="currentColor"
          viewBox="0 0 24 24"
        >
          <path
            stroke-linecap="round"
            stroke-linejoin="round"
            stroke-width="2"
            d="M4 4v5h.582M20 20v-5h-.581M5 9a9 9 0 0114.416-5.59M19 15a9 9 0 01-14.416 5.59"
          />
        </svg>
      </button>
    </div>

    <!-- Input and select -->
    <div class="flex items-center space-x-2">
      <input
        type="text"
        placeholder="150.000"
        class="flex-1 p-3 border rounded-lg bg-gray-100 focus:outline-none focus:ring focus:ring-blue-200"
      />
      <select
        class="border rounded-lg px-3 py-2 bg-gray-100 focus:outline-none"
      >
        <option>EUR</option>
        <option>RON</option>
      </select>
    </div>

    <!-- Tax toggle -->
    <div class="flex items-center justify-between">
      <span class="text-sm font-medium">Tax is applied</span>
      <label class="relative inline-flex items-center cursor-pointer">
        <input type="checkbox" value="" class="sr-only peer" checked />
        <div
          class="w-11 h-6 bg-gray-200 peer-focus:outline-none peer-focus:ring-2 peer-focus:ring-blue-400 rounded-full peer dark:bg-gray-300 peer-checked:after:translate-x-full peer-checked:after:border-white after:content-[''] after:absolute after:top-[2px] after:left-[2px] after:bg-white after:border-gray-300 after:border after:rounded-full after:h-5 after:w-5 after:transition-all peer-checked:bg-blue-900"
        ></div>
      </label>
    </div>

    <!-- Tax dropdown -->
    <select
      class="w-full border rounded-lg px-3 py-2 bg-gray-100 focus:outline-none"
    >
      <option>1%</option>
      <option>2%</option>
      <option>3%</option>
    </select>

    <!-- Tarif CF -->
    <div>
      <label class="block text-sm font-medium mb-1">Tarif CF</label>
      <div class="flex flex-col gap-2 p-3 bg-gray-100 rounded-lg">
        <label class="inline-flex items-center">
          <input type="radio" name="tarif" class="form-radio text-blue-900" />
          <span class="ml-2">PF</span>
        </label>
        <label class="inline-flex items-center">
          <input
            type="radio"
            name="tarif"
            checked
            class="form-radio text-blue-900"
          />
          <span class="ml-2">PJ</span>
        </label>
      </div>
    </div>

    <!-- Buttons -->
    <div class="flex gap-4">
      <button
        class="flex-1 bg-blue-900 text-white py-2 rounded-lg font-medium hover:bg-blue-800"
      >
        Calculate
      </button>
      <button
        class="flex-1 bg-white text-gray-600 border py-2 rounded-lg font-medium hover:bg-gray-100"
      >
        Reset
      </button>
    </div>
  </Card>
</div>
</template>