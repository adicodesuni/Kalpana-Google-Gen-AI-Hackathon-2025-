import React, { useState, useRef } from 'react';
import { Button } from "/components/ui/button";
import { Card, CardContent, CardDescription, CardHeader, CardTitle } from "/components/ui/card";
import { Input } from "/components/ui/input";
import { Label } from "/components/ui/label";
import { Textarea } from "@/components/ui/textarea";

const ProjectKalpanaPrototype = () => {
  const [currentStep, setCurrentStep] = useState('upload');
  const [selectedImage, setSelectedImage] = useState<string | null>(null);
  const [craftType, setCraftType] = useState('');
  const [generatedStory, setGeneratedStory] = useState('');
  const [translatedStory, setTranslatedStory] = useState('');
  const [language, setLanguage] = useState('en');
  const [isLoading, setIsLoading] = useState(false);
  const fileInputRef = useRef<HTMLInputElement>(null);

  const handleImageUpload = (e: React.ChangeEvent<HTMLInputElement>) => {
    if (e.target.files && e.target.files[0]) {
      const file = e.target.files[0];
      const reader = new FileReader();
      reader.onload = (event) => {
        setSelectedImage(event.target?.result as string);
        setCurrentStep('analyze');
      };
      reader.readAsDataURL(file);
    }
  };

  const simulateAnalysis = () => {
    setIsLoading(true);
    setTimeout(() => {
      setCraftType('Handwoven Textile');
      setGeneratedStory('This beautiful handwoven textile showcases intricate patterns that reflect generations of traditional craftsmanship. Each thread tells a story of cultural heritage, with motifs that symbolize prosperity and harmony. The artisan has skillfully combined natural dyes to create a vibrant tapestry that connects the past with the present.');
      setTranslatedStory('');
      setIsLoading(false);
      setCurrentStep('story');
    }, 2000);
  };

  const simulateTranslation = () => {
    setIsLoading(true);
    setTimeout(() => {
      if (language === 'hi') {
        setTranslatedStory('यह सुंदर हथकरघा वस्त्र जटिल पैटर्न प्रदर्शित करता है जो पीढ़ियों की पारंपरिक कारीगरी को दर्शाता है। प्रत्येक धागा सांस्कृतिक विरासत की कहानी कहता है, जिसमें रूपांकन समृद्धि और सद्भाव का प्रतीक हैं। कारीगर ने प्राकृतिक रंगों को कुशलता से संयोजित किया है ताकि एक जीवंत टेपेस्ट्री बनाई जा सके जो अतीत को वर्तमान से जोड़ती है।');
      } else if (language === 'es') {
        setTranslatedStory('Este hermoso textil tejido a mano muestra intrincados patrones que reflejan generaciones de artesanía tradicional. Cada hilo cuenta una historia de herencia cultural, con motivos que simbolizan prosperidad y armonía. El artesano ha combinado hábilmente tintes naturales para crear un tapiz vibrante que conecta el pasado con el presente.');
      }
      setIsLoading(false);
    }, 1500);
  };

  const handleShare = () => {
    setIsLoading(true);
    setTimeout(() => {
      alert('Story shared successfully!');
      setIsLoading(false);
    }, 1000);
  };

  const handleNewUpload = () => {
    setSelectedImage(null);
    setCraftType('');
    setGeneratedStory('');
    setTranslatedStory('');
    setCurrentStep('upload');
    if (fileInputRef.current) {
      fileInputRef.current.value = '';
    }
  };

  return (
    <div className="min-h-screen bg-gradient-to-b from-blue-50 to-indigo-100 p-4 md:p-8">
      <div className="max-w-4xl mx-auto">
        {/* Header */}
        <header className="text-center mb-8">
          <h1 className="text-4xl font-bold text-indigo-800 mb-2">Project Kalpana</h1>
          <p className="text-lg text-indigo-600">Empowering artisans through digital storytelling</p>
          
          {/* Progress Steps */}
          <div className="flex justify-center my-6">
            <div className={`flex items-center ${currentStep !== 'upload' ? 'text-indigo-600' : 'text-gray-400'}`}>
              <div className={`w-8 h-8 rounded-full flex items-center justify-center ${currentStep !== 'upload' ? 'bg-indigo-100 text-indigo-700' : 'bg-gray-200 text-gray-600'}`}>
                1
              </div>
              <span className="ml-2">Upload</span>
            </div>
            
            <div className={`mx-4 h-0.5 w-12 ${currentStep !== 'upload' ? 'bg-indigo-400' : 'bg-gray-300'}`}></div>
            
            <div className={`flex items-center ${currentStep === 'story' || currentStep === 'share' ? 'text-indigo-600' : 'text-gray-400'}`}>
              <div className={`w-8 h-8 rounded-full flex items-center justify-center ${currentStep === 'story' || currentStep === 'share' ? 'bg-indigo-100 text-indigo-700' : 'bg-gray-200 text-gray-600'}`}>
                2
              </div>
              <span className="ml-2">Story</span>
            </div>
            
            <div className={`mx-4 h-0.5 w-12 ${currentStep === 'share' ? 'bg-indigo-400' : 'bg-gray-300'}`}></div>
            
            <div className={`flex items-center ${currentStep === 'share' ? 'text-indigo-600' : 'text-gray-400'}`}>
              <div className={`w-8 h-8 rounded-full flex items-center justify-center ${currentStep === 'share' ? 'bg-indigo-100 text-indigo-700' : 'bg-gray-200 text-gray-600'}`}>
                3
              </div>
              <span className="ml-2">Share</span>
            </div>
          </div>
        </header>

        {/* Main Content */}
        <main>
          {currentStep === 'upload' && (
            <Card className="w-full">
              <CardHeader>
                <CardTitle>Upload Craft Image</CardTitle>
                <CardDescription>
                  Upload an image of your craft to begin creating its digital story
                </CardDescription>
              </CardHeader>
              <CardContent>
                <div className="space-y-4">
                  <div className="grid w-full items-center gap-1.5">
                    <Label htmlFor="picture">Craft Image</Label>
                    <Input 
                      id="picture" 
                      type="file" 
                      ref={fileInputRef}
                      onChange={handleImageUpload} 
                      accept="image/*"
                    />
                  </div>
                  
                  <div className="mt-6 border-2 border-dashed border-indigo-300 rounded-lg p-8 text-center bg-indigo-50">
                    <p className="text-indigo-700 mb-4">Drag and drop your image here or click to browse</p>
                    <Button onClick={() => fileInputRef.current?.click()}>
                      Select Image
                    </Button>
                  </div>
                  
                  <div className="mt-6">
                    <img 
                      src="https://placeholder-image-service.onrender.com/image/400x300?prompt=Handcrafted%20textile%20with%20intricate%20patterns%20and%20vibrant%20colors&id=c023d693-0298-4553-9676-26c9e4adc581" 
                      alt="Example of a handcrafted textile with intricate patterns and vibrant colors" 
                      className="rounded-lg shadow-md mx-auto"
                    />
                    <p className="text-center text-sm text-muted-foreground mt-2">Example: Handwoven textile</p>
                  </div>
                </div>
              </CardContent>
            </Card>
          )}

          {currentStep === 'analyze' && (
            <Card className="w-full">
              <CardHeader>
                <CardTitle>Analyzing Your Craft</CardTitle>
                <CardDescription>
                  We're detecting patterns and understanding the cultural significance of your craft
                </CardDescription>
              </CardHeader>
              <CardContent>
                <div className="flex flex-col md:flex-row gap-6">
                  <div className="md:w-1/2">
                    {selectedImage && (
                      <img 
                        src={selectedImage} 
                        alt="Uploaded craft for analysis" 
                        className="rounded-lg shadow-md w-full"
                      />
                    )}
                  </div>
                  
                  <div className="md:w-1/2 flex flex-col justify-center">
                    {isLoading ? (
                      <div className="text-center">
                        <div className="animate-spin rounded-full h-12 w-12 border-b-2 border-indigo-600 mx-auto mb-4"></div>
                        <p>Analyzing craft patterns and cultural elements...</p>
                      </div>
                    ) : (
                      <Button onClick={simulateAnalysis} className="w-full">
                        Generate Story
                      </Button>
                    )}
                  </div>
                </div>
              </CardContent>
            </Card>
          )}

          {currentStep === 'story' && (
            <Card className="w-full">
              <CardHeader>
                <CardTitle>Your Craft's Story</CardTitle>
                <CardDescription>
                  Based on our analysis of your craft, here's its unique story
                </CardDescription>
              </CardHeader>
              <CardContent>
                <div className="space-y-6">
                  <div className="flex flex-col md:flex-row gap-6">
                    <div className="md:w-1/2">
                      {selectedImage && (
                        <img 
                          src={selectedImage} 
                          alt="Uploaded craft with cultural significance" 
                          className="rounded-lg shadow-md w-full"
                        />
                      )}
                    </div>
                    
                    <div className="md:w-1/2">
                      <div className="mb-4">
                        <Label htmlFor="craft-type">Detected Craft Type</Label>
                        <Input 
                          id="craft-type" 
                          value={craftType} 
                          readOnly 
                          className="mt-1 bg-muted"
                        />
                      </div>
                      
                      <div className="mb-4">
                        <Label htmlFor="story">Generated Story</Label>
                        <Textarea 
                          id="story" 
                          value={generatedStory} 
                          readOnly 
                          className="mt-1 h-32 bg-muted"
                        />
                      </div>
                      
                      <div className="mb-4">
                        <Label htmlFor="language">Translate Story</Label>
                        <select 
                          id="language"
                          value={language}
                          onChange={(e) => setLanguage(e.target.value)}
                          className="w-full p-2 border rounded-md mt-1"
                        >
                          <option value="en">English</option>
                          <option value="hi">Hindi</option>
                          <option value="es">Spanish</option>
                        </select>
                        
                        <Button 
                          onClick={simulateTranslation} 
                          disabled={isLoading}
                          variant="outline" 
                          className="mt-2 w-full"
                        >
                          {isLoading ? 'Translating...' : 'Translate'}
                        </Button>
                      </div>
                      
                      {translatedStory && (
                        <div className="mb-4">
                          <Label htmlFor="translated-story">Translated Story</Label>
                          <Textarea 
                            id="translated-story" 
                            value={translatedStory} 
                            readOnly 
                            className="mt-1 h-32 bg-muted"
                          />
                        </div>
                      )}
                    </div>
                  </div>
                  
                  <div className="flex gap-4 justify-end">
                    <Button variant="outline" onClick={handleNewUpload}>
                      New Upload
                    </Button>
                    <Button onClick={() => setCurrentStep('share')}>
                      Continue to Share
                    </Button>
                  </div>
                </div>
              </CardContent>
            </Card>
          )}

          {currentStep === 'share' && (
            <Card className="w-full">
              <CardHeader>
                <CardTitle>Share Your Craft's Story</CardTitle>
                <CardDescription>
                  Share your craft's digital story on social media or archive it for future use
                </CardDescription>
              </CardHeader>
              <CardContent>
                <div className="space-y-6">
                  <div className="border rounded-lg p-4 bg-white">
                    <div className="flex flex-col md:flex-row gap-4">
                      <div className="md:w-1/3">
                        {selectedImage && (
                          <img 
                            src={selectedImage} 
                            alt="Craft to be shared on social media" 
                            className="rounded-lg w-full"
                          />
                        )}
                      </div>
                      <div className="md:w-2/3">
                        <h3 className="font-semibold text-lg mb-2">{craftType}</h3>
                        <p className="text-sm text-muted-foreground">
                          {generatedStory.length > 150 ? `${generatedStory.substring(0, 150)}...` : generatedStory}
                        </p>
                        <div className="mt-4 flex items-center">
                          <div className="w-6 h-6 rounded-full bg-indigo-100 flex items-center justify-center mr-2">
                            <span className="text-xs text-indigo-700">K</span>
                          </div>
                          <span className="text-sm text-indigo-600">Project Kalpana</span>
                        </div>
                      </div>
                    </div>
                  </div>
                  
                  <div className="grid grid-cols-2 md:grid-cols-4 gap-4">
                    <Button variant="outline" className="flex flex-col h-16">
                      <span>Instagram</span>
                    </Button>
                    <Button variant="outline" className="flex flex-col h-16">
                      <span>Facebook</span>
                    </Button>
                    <Button variant="outline" className="flex flex-col h-16">
                      <span>Twitter</span>
                    </Button>
                    <Button variant="outline" className="flex flex-col h-16">
                      <span>WhatsApp</span>
                    </Button>
                  </div>
                  
                  <div className="flex items-center">
                    <input 
                      type="checkbox" 
                      id="consent" 
                      className="mr-2" 
                    />
                    <Label htmlFor="consent">
                      I give consent to archive this craft story for cultural preservation and research purposes
                    </Label>
                  </div>
                  
                  <div className="flex gap-4 justify-end">
                    <Button variant="outline" onClick={() => setCurrentStep('story')}>
                      Back
                    </Button>
                    <Button onClick={handleShare} disabled={isLoading}>
                      {isLoading ? 'Sharing...' : 'Share Story'}
                    </Button>
                  </div>
                </div>
              </CardContent>
            </Card>
          )}
        </main>

        {/* Footer */}
        <footer className="mt-8 text-center text-sm text-muted-foreground">
          <p>Project Kalpana - Bridging traditional craftsmanship with digital storytelling</p>
        </footer>
      </div>
    </div>
  );
};

export default ProjectKalpanaPrototype;
