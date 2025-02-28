# Resume-Search-API
**React-based Job Search API code that integrates with LinkedIn, Monster, and Dice sourcing.**
This API has been created completely by ChatGPT. I have created this for future preference job posting website which I am planning to launch.
import { useState } from "react";
import { Input } from "@/components/ui/input";
import { Button } from "@/components/ui/button";
import { Card, CardContent } from "@/components/ui/card";
import { Linkedin, Globe, Search } from "lucide-react";

export default function JobSearch() {
  const [query, setQuery] = useState("");

  const handleSearch = () => {
    if (query) {
      alert(`Searching jobs for: ${query}`);
    }
  };

  return (
    <div className="max-w-2xl mx-auto mt-10 p-4 border rounded-lg shadow-lg bg-white">
      <h2 className="text-xl font-bold mb-4">Job Search</h2>
      <div className="flex gap-2">
        <Input
          type="text"
          placeholder="Enter job title, skills, or keywords..."
          value={query}
          onChange={(e) => setQuery(e.target.value)}
        />
        <Button onClick={handleSearch}>
          <Search className="w-5 h-5" />
        </Button>
      </div>
      
      <div className="mt-6 flex justify-around">
        <Card className="p-2 cursor-pointer hover:bg-gray-100" onClick={() => window.open(`https://www.linkedin.com/jobs/search/?keywords=${query}`, "_blank") }>
          <CardContent className="flex flex-col items-center">
            <Linkedin className="w-10 h-10 text-blue-600" />
            <span className="text-sm font-medium">LinkedIn</span>
          </CardContent>
        </Card>

        <Card className="p-2 cursor-pointer hover:bg-gray-100" onClick={() => window.open(`https://www.monster.com/jobs/search/?q=${query}`, "_blank") }>
          <CardContent className="flex flex-col items-center">
            <Globe className="w-10 h-10 text-red-500" />
            <span className="text-sm font-medium">Monster</span>
          </CardContent>
        </Card>

        <Card className="p-2 cursor-pointer hover:bg-gray-100" onClick={() => window.open(`https://www.dice.com/jobs?q=${query}`, "_blank") }>
          <CardContent className="flex flex-col items-center">
            <Globe className="w-10 h-10 text-green-500" />
            <span className="text-sm font-medium">Dice</span>
          </CardContent>
        </Card>
      </div>
    </div>
  );
}
