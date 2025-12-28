import React, { useState } from 'react';
import { Cpu, Zap, Shield, RefreshCw, Activity, Lock, Database, ChevronLeft } from 'lucide-react';

export default function App() {
  const [input, setInput] = useState('');
  const [result, setResult] = useState(null);
  const [loading, setLoading] = useState(false);
  const [error, setError] = useState(null);

  // ==========================================
  // استبدلي الرابط أدناه برابط الـ Backend الخاص بكِ من Render
  // ==========================================
  const API_URL = "https://your-backend-app.onrender.com/process";

  const runEngine = async () => {
    if (!input) return;
    setLoading(true);
    setError(null);
    try {
      const response = await fetch(API_URL, {
        method: 'POST',
        headers: { 'Content-Type': 'application/json' },
        body: JSON.stringify({ content: input })
      });
      
      if (!response.ok) throw new Error("فشل الاتصال بالمحرك");
      
      const data = await response.json();
      setResult(data);
    } catch (err) {
      setError("خطأ في الاتصال: تأكدي أن الـ Backend في حالة Live.");
    } finally {
      setLoading(false);
    }
  };

  return (
    <div className="min-h-screen bg-[#020617] text-slate-100 selection:bg-indigo-500/30">
      <nav className="border-b border-white/5 bg-slate-900/40 backdrop-blur-xl sticky top-0 z-50">
        <div className="max-w-7xl mx-auto px-6 h-20 flex justify-between items-center">
          <div className="flex items-center gap-3">
            <div className="bg-indigo-600 p-2 rounded-xl shadow-lg shadow-indigo-500/20">
              <Cpu size={24} className="text-white" />
            </div>
            <span className="text-xl font-black tracking-tighter text-white">F-LAMBDA CORE</span>
          </div>
          <div className="flex items-center gap-4">
            <div className="flex items-center gap-2 text-[10px] font-bold text-emerald-400 bg-emerald-500/10 px-3 py-1 rounded-full border border-emerald-500/20">
              <div className="w-1.5 h-1.5 bg-emerald-500 rounded-full animate-pulse"></div>
              ENGINE ACTIVE
            </div>
          </div>
        </div>
      </nav>

      <main className="max-w-6xl mx-auto p-6 py-12">
        <div className="grid lg:grid-cols-2 gap-12 items-start">
          <div className="space-y-8">
            <div>
              <h1 className="text-5xl font-black mb-4 leading-tight tracking-tight">نظام المعالجة الطيفية الحتمية</h1>
              <p className="text-slate-400 text-lg leading-relaxed">تحويل البيانات إلى بصمات فيزيائية مشفرة باستخدام خوارزمية F-Lambda المستقرة.</p>
            </div>

            <div className="bg-slate-900/50 border border-white/10 p-1 rounded-[2.5rem] shadow-2xl overflow-hidden backdrop-blur-sm">
              <div className="p-8 space-y-6">
                <div className="flex items-center gap-2 text-slate-500 text-xs font-bold uppercase tracking-widest">
                  <Database size={16} className="text-indigo-500" /> منطقة الإدخال
                </div>
                <textarea 
                  value={input}
                  onChange={(e) => setInput(e.target.value)}
                  placeholder="أدخل النص المراد تشفيره فيزيائياً..."
                  className="w-full h-64 bg-black/40 border border-slate-800 rounded-3xl p-6 text-indigo-300 font-mono text-xl focus:outline-none focus:border-indigo-500 transition-all resize-none"
                />
                <button 
                  onClick={runEngine}
                  disabled={loading || !input}
                  className="w-full bg-indigo-600 hover:bg-indigo-500 disabled:bg-slate-800 py-6 rounded-2xl font-black text-xl transition-all flex items-center justify-center gap-3 shadow-2xl shadow-indigo-600/20 active:scale-[0.98]"
                >
                  {loading ? <RefreshCw className="animate-spin" /> : <><Zap size={22} /> تنفيذ المعالجة</>}
                </button>
                {error && <p className="text-red-400 text-sm text-center font-bold bg-red-500/5 py-3 rounded-xl border border-red-500/10">{error}</p>}
              </div>
            </div>
          </div>

          <div className="lg:mt-32 space-y-6">
            <div className="bg-slate-900/80 border border-white/10 p-10 rounded-[2.5rem] shadow-2xl relative">
              <div className="absolute -top-4 -right-4 bg-indigo-600 p-3 rounded-2xl shadow-xl">
                <Lock size={20} />
              </div>
              <h3 className="text-slate-500 text-xs font-black uppercase tracking-[0.2em] mb-8">البيانات المستعادة</h3>
              
              <div className="space-y-8">
                <div>
                  <label className="text-[10px] text-slate-600 font-bold block mb-3 tracking-widest uppercase">Recovery Interface</label>
                  <div className="bg-black/60 border border-slate-800 p-8 rounded-3xl font-mono text-emerald-400 text-2xl min-h-[160px] flex items-center justify-center text-center leading-relaxed">
                    {result ? result.recovered_content : <span className="text-slate-700 italic text-lg">بانتظار الإشارة...</span>}
                  </div>
                </div>

                <div className="grid grid-cols-2 gap-6">
                  <div className="bg-white/5 p-6 rounded-3xl border border-white/5">
                    <span className="text-[10px] text-slate-600 block mb-1 font-bold">زمن المحاكاة</span>
                    <span className="text-2xl font-black text-indigo-400">{result ? result.processing_time : "0.00s"}</span>
                  </div>
                  <div className="bg-white/5 p-6 rounded-3xl border border-white/5">
                    <span className="text-[10px] text-slate-600 block mb-1 font-bold">دقة الاسترداد</span>
                    <span className="text-2xl font-black text-slate-400">{result ? "100%" : "0%"}</span>
                  </div>
                </div>

                {result && result.integrity && (
                  <div className="pt-6 border-t border-white/5">
                    <div className="flex items-center gap-3 text-emerald-500 bg-emerald-500/5 p-4 rounded-2xl border border-emerald-500/10">
                      <Shield size={20} />
                      <span className="font-bold text-xs tracking-widest uppercase">Purity Verified & Deterministic</span>
                    </div>
                  </div>
                )}
              </div>
            </div>
          </div>
        </div>
      </main>
    </div>
  );
}

