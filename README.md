import React, { useState } from "react"; import { Card, CardContent } from "@/components/ui/card"; import { Button } from "@/components/ui/button";

export default function Home() { const [coins, setCoins] = useState(100); const [videos, setVideos] = useState([]); const [newVideo, setNewVideo] = useState(""); const [videoCoins, setVideoCoins] = useState(10);

const handleAddVideo = () => { if (newVideo && videoCoins <= coins) { setVideos([...videos, { url: newVideo, coins: videoCoins }]); setCoins(coins - videoCoins); setNewVideo(""); setVideoCoins(10); } };

return ( <div className="p-4 max-w-2xl mx-auto"> <h1 className="text-2xl font-bold mb-4">YouTube Boosting Platform (Demo)</h1>

<Card className="mb-4">
    <CardContent className="p-4">
      <p className="mb-2">Available Coins: <strong>{coins}</strong></p>
      <input
        type="text"
        placeholder="Enter YouTube video URL"
        className="border p-2 w-full mb-2"
        value={newVideo}
        onChange={(e) => setNewVideo(e.target.value)}
      />
      <input
        type="number"
        min="1"
        max={coins}
        className="border p-2 w-full mb-2"
        value={videoCoins}
        onChange={(e) => setVideoCoins(Number(e.target.value))}
      />
      <Button onClick={handleAddVideo}>Add Video for Boost</Button>
    </CardContent>
  </Card>

  <h2 className="text-xl font-semibold mb-2">Your Boosted Videos</h2>
  {videos.map((video, index) => (
    <Card key={index} className="mb-2">
      <CardContent className="p-4">
        <p>URL: {video.url}</p>
        <p>Assigned Coins: {video.coins}</p>
      </CardContent>
    </Card>
  ))}
</div>

); }

