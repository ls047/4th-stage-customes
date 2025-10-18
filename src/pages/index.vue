    <template>
    <motion.div
        class="min-h-screen bg-gradient-to-br from-gray-950 via-red-950 to-gray-950 text-gray-100 relative overflow-hidden"
        :initial="{ opacity: 0, y: 0 }"
        :animate="{ opacity: 1, y: 0 }"
        :transition="{ duration: 0.5, ease: 'easeInOut' }"
    >
        <!-- Header -->
        <div dir="rtl" class="container mx-auto px-4 py-4 md:py-8">
            <motion.div
                class="text-center mb-6 md:mb-12"
                :initial="{ opacity: 0, y: 20 }"
                :animate="{ opacity: 1, y: 0 }"
                :transition="{ delay: 0.3, duration: 0.8 }"
            >
                <h1 class="text-2xl md:text-4xl lg:text-6xl font-bold mb-2 md:mb-4 bg-gradient-to-r from-red-400 to-orange-400 bg-clip-text text-transparent">
                    مولد مقاسات الطلاب
                </h1>
                <p class="text-sm md:text-xl text-gray-300 max-w-2xl mx-auto px-4">
                    أدخل مقاساتك لتوليد ملف يمكن إرساله لمحل الملابس
                </p>
            </motion.div>

            <!-- Form Container -->
            <motion.div
                class="max-w-4xl mx-auto bg-gray-900/50 backdrop-blur-sm rounded-2xl border border-gray-700 p-4 md:p-8 shadow-2xl"
                :initial="{ opacity: 0, scale: 0.95 }"
                :animate="{ opacity: 1, scale: 1 }"
                :transition="{ delay: 0.5, duration: 0.8 }"
            >
                <form @submit.prevent="generateFile" class="space-y-4 md:space-y-8">
                    <!-- Student Information -->
                    <div class="grid grid-cols-1 md:grid-cols-2 gap-4 md:gap-6">
                        <div>
                            <label class="block text-base md:text-lg font-semibold text-gray-200 mb-2 md:mb-3">
                                اسم الطالب
                            </label>
                            <input
                                v-model="formData.studentName"
                                type="text"
                                required
                                class="w-full px-3 md:px-4 py-2 md:py-3 bg-gray-800 border border-gray-600 rounded-lg focus:ring-2 focus:ring-red-500 focus:border-transparent text-gray-100 placeholder-gray-400 text-sm md:text-base"
                                placeholder="أدخل اسمك"
                            />
                        </div>
                        <div>
                            <label class="block text-base md:text-lg font-semibold text-gray-200 mb-2 md:mb-3">
                                رقم الطالب
                            </label>
                            <input
                                v-model="formData.studentNumber"
                                type="text"
                                required
                                class="w-full px-3 md:px-4 py-2 md:py-3 bg-gray-800 border border-gray-600 rounded-lg focus:ring-2 focus:ring-red-500 focus:border-transparent text-gray-100 placeholder-gray-400 text-sm md:text-base"
                                placeholder="أدخل رقمك"
                            />
                        </div>
                    </div>

                    <!-- Body Measurements -->
                    <div class="space-y-4 md:space-y-6">
                        <h3 class="text-lg md:text-2xl font-bold text-gray-200 border-b border-gray-600 pb-2">
                            المقاسات الجسدية
                        </h3>

                        <div class="grid grid-cols-1 md:grid-cols-2 gap-4 md:gap-6">
                            <div>
                                <label class="block text-base md:text-lg font-semibold text-gray-200 mb-2 md:mb-3">
                                    طول الردن
                                </label>
                                <input
                                    v-model="formData.waistLength"
                                    type="text"
                                    required
                                    class="w-full px-3 md:px-4 py-2 md:py-3 bg-gray-800 border border-gray-600 rounded-lg focus:ring-2 focus:ring-red-500 focus:border-transparent text-gray-100 placeholder-gray-400 text-sm md:text-base"
                                    placeholder="أدخل طول الردن"
                                />
                            </div>

                            <div>
                                <label class="block text-base md:text-lg font-semibold text-gray-200 mb-2 md:mb-3">
                                    الطول
                                </label>
                                <input
                                    v-model="formData.height"
                                    type="text"
                                    required
                                    class="w-full px-3 md:px-4 py-2 md:py-3 bg-gray-800 border border-gray-600 rounded-lg focus:ring-2 focus:ring-red-500 focus:border-transparent text-gray-100 placeholder-gray-400 text-sm md:text-base"
                                    placeholder="أدخل الطول"
                                />
                            </div>

                            <div>
                                <label class="block text-base md:text-lg font-semibold text-gray-200 mb-2 md:mb-3">
                                    عرض الجتف
                                </label>
                                <input
                                    v-model="formData.shoulderWidth"
                                    type="text"
                                    required
                                    class="w-full px-3 md:px-4 py-2 md:py-3 bg-gray-800 border border-gray-600 rounded-lg focus:ring-2 focus:ring-red-500 focus:border-transparent text-gray-100 placeholder-gray-400 text-sm md:text-base"
                                    placeholder="أدخل عرض الجتف"
                                />
                            </div>

                            <div>
                                <label class="block text-base md:text-lg font-semibold text-gray-200 mb-2 md:mb-3">
                                    قياس الرأس
                                </label>
                                <input
                                    v-model="formData.headSize"
                                    type="text"
                                    required
                                    class="w-full px-3 md:px-4 py-2 md:py-3 bg-gray-800 border border-gray-600 rounded-lg focus:ring-2 focus:ring-red-500 focus:border-transparent text-gray-100 placeholder-gray-400 text-sm md:text-base"
                                    placeholder="أدخل قياس الرأس"
                                />
                            </div>
                        </div>
                    </div>

                    <!-- Clothing Choices -->
                    <div class="space-y-4 md:space-y-6">
                        <h3 class="text-lg md:text-2xl font-bold text-gray-200 border-b border-gray-600 pb-2">
                            خيارات الملابس
                        </h3>

                        <div>
                            <label class="block text-base md:text-lg font-semibold text-gray-200 mb-2 md:mb-3">
                                نوع القطعة
                            </label>
                            <div class="flex flex-col sm:flex-row gap-2 md:gap-4">
                                <label class="flex items-center space-x-3 cursor-pointer">
                                    <input
                                        v-model="formData.clothingType"
                                        type="radio"
                                        value="ملكي"
                                        class="w-5 h-5 text-red-500 bg-gray-800 border-gray-600 focus:ring-red-500"
                                    />
                                    <span class="text-gray-200 text-sm md:text-lg">ملكي</span>
                                </label>
                                <label class="flex items-center space-x-3 cursor-pointer">
                                    <input
                                        v-model="formData.clothingType"
                                        type="radio"
                                        value="امريكي"
                                        class="w-5 h-5 text-red-500 bg-gray-800 border-gray-600 focus:ring-red-500"
                                    />
                                    <span class="text-gray-200 text-sm md:text-lg">امريكي</span>
                                </label>
                            </div>
                        </div>

                    </div>

                    <!-- Additional Notes -->
                    <div>
                        <label class="block text-lg font-semibold text-gray-200 mb-3">
                            ملاحظات إضافية (اختياري)
                        </label>
                        <textarea
                            v-model="formData.additionalNotes"
                            rows="3"
                            class="w-full px-4 py-3 bg-gray-800 border border-gray-600 rounded-lg focus:ring-2 focus:ring-red-500 focus:border-transparent text-gray-100 placeholder-gray-400 resize-none"
                            placeholder="أي ملاحظات إضافية حول المقاسات أو التفضيلات..."
                        ></textarea>
                    </div>

                    <!-- Note Section -->
                    <div class="bg-blue-900/30 border border-blue-700 rounded-lg p-3 md:p-4">
                        <div class="flex items-center space-x-3">
                            <div class="w-2 h-2 bg-blue-400 rounded-full"></div>
                            <p class="text-blue-200 text-sm md:text-lg">
                                <strong>ملاحظة:</strong> الوشاح مثلث وسط
                            </p>
                        </div>
                    </div>

                    <!-- Action Buttons -->
                    <div class="text-center pt-4 md:pt-6 space-y-3">
                        <motion.button
                            type="submit"
                            class="bg-gradient-to-r from-red-500 to-orange-500 hover:from-red-600 hover:to-orange-600 text-white font-bold py-3 md:py-4 px-6 md:px-8 rounded-xl text-sm md:text-lg transition-all duration-300 transform hover:scale-105 shadow-lg"
                            :whileHover="{ scale: 1.05 }"
                            :whileTap="{ scale: 0.95 }"
                        >
                            توليد ملف المقاسات
                        </motion.button>

                        <div class="flex justify-center">
                            <motion.button
                                type="button"
                                @click="clearSavedData"
                                class="bg-gray-600 hover:bg-gray-700 text-white font-medium py-2 px-4 rounded-lg text-sm transition-all duration-300"
                                :whileHover="{ scale: 1.02 }"
                                :whileTap="{ scale: 0.98 }"
                            >
                                مسح البيانات المحفوظة
                            </motion.button>
                        </div>
                    </div>
                </form>
            </motion.div>
        </div>
    </motion.div>
    </template>

    <script setup lang="ts">
    import { motion } from 'motion-v'
import { reactive, watch, onMounted } from 'vue'

    // Add component name
    defineOptions({
    name: 'SizeGenerator',
})

// Form data
const formData = reactive({
    studentName: '',
    studentNumber: '',
    waistLength: '',
    height: '',
    shoulderWidth: '',
    headSize: '',
    clothingType: '',
    additionalNotes: ''
})

// Save data to localStorage
const saveToStorage = () => {
    localStorage.setItem('sizeGeneratorData', JSON.stringify(formData))
}

// Load data from localStorage
const loadFromStorage = () => {
    const savedData = localStorage.getItem('sizeGeneratorData')
    if (savedData) {
        try {
            const parsedData = JSON.parse(savedData)
            Object.assign(formData, parsedData)
        } catch (error) {
            console.error('Error loading saved data:', error)
        }
    }
}

// Clear all saved data
const clearSavedData = () => {
    localStorage.removeItem('sizeGeneratorData')
    Object.keys(formData).forEach(key => {
        (formData as any)[key] = ''
    })
}

// Watch for changes and auto-save
watch(formData, () => {
    saveToStorage()
}, { deep: true })

// Load data on component mount
onMounted(() => {
    loadFromStorage()
})

// Generate file function
const generateFile = () => {
    // Create text content with RTL formatting
    let textContent = ''

    // Add RTL marker at the beginning
    textContent += '\u202B' // Right-to-left embedding

    // Header with cleaner spacing
    textContent += '\n'
    textContent += '═'.repeat(50) + '\n'
    textContent += '           مقاسات الطالب\n'
    textContent += '═'.repeat(50) + '\n'
    textContent += '\n'

    // Student info section
    textContent += 'معلومات الطالب:\n'
    textContent += '─'.repeat(30) + '\n'
    textContent += `الاسم: ${formData.studentName}\n`
    textContent += `الرقم: ${formData.studentNumber}\n`
    textContent += `التاريخ: ${new Date().toLocaleDateString('ar-SA')}\n`
    textContent += '\n'

    // Measurements section
    textContent += 'المقاسات الجسدية:\n'
    textContent += '─'.repeat(30) + '\n'
    textContent += `طول الردن: ${formData.waistLength}\n`
    textContent += `الطول: ${formData.height}\n`
    textContent += `عرض الجتف: ${formData.shoulderWidth}\n`
    textContent += `قياس الرأس: ${formData.headSize}\n`
    textContent += '\n'

    // Clothing section
    textContent += 'خيارات الملابس:\n'
    textContent += '─'.repeat(30) + '\n'
    textContent += `نوع القطعة: ${formData.clothingType}\n`
    textContent += '\n'

    // Notes section
    if (formData.additionalNotes) {
        textContent += 'ملاحظات إضافية:\n'
        textContent += '─'.repeat(30) + '\n'
        textContent += `${formData.additionalNotes}\n`
        textContent += '\n'
    }

    // Footer
    textContent += '═'.repeat(50) + '\n'
    textContent += 'تم توليد هذا الملف بواسطة مولد مقاسات الطلاب\n'
    textContent += '═'.repeat(50) + '\n'

    // Create and download text file with RTL support
    const blob = new Blob([textContent], { type: 'text/plain;charset=utf-8' })
    const url = URL.createObjectURL(blob)
    const link = document.createElement('a')
    link.href = url
    link.download = `مقاسات_${formData.studentName}_${formData.studentNumber}.txt`
    document.body.appendChild(link)
    link.click()
    document.body.removeChild(link)
    URL.revokeObjectURL(url)
}
    </script>

    <style scoped>
/* Custom scrollbar */
::-webkit-scrollbar {
    width: 8px;
}

::-webkit-scrollbar-track {
    background: #1f2937;
}

::-webkit-scrollbar-thumb {
    background: #ef4444;
    border-radius: 4px;
}

::-webkit-scrollbar-thumb:hover {
    background: #dc2626;
}
    </style>
