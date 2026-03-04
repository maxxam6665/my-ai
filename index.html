import { useState, useRef, useEffect } from "react";

const MODEL = "claude-sonnet-4-20250514";

function formatText(text) {
  const parts = [];
  const codeBlockRegex = /```(\w+)?\n([\s\S]*?)```/g;
  let last = 0, match;
  while ((match = codeBlockRegex.exec(text)) !== null) {
    if (match.index > last) parts.push({ type: "text", content: text.slice(last, match.index) });
    parts.push({ type: "code", lang: match[1] || "", content: match[2].trim() });
    last = match.index + match[0].length;
  }
  if (last < text.length) parts.push({ type: "text", content: text.slice(last) });
  return parts;
}

function InlineText({ text }) {
  const html = text
    .replace(/`([^`]+)`/g, '<code>$1</code>')
    .replace(/\*\*([^*]+)\*\*/g, '<b>$1</b>')
    .replace(/\n/g, '<br/>');
  return <span dangerouslySetInnerHTML={{ __html: html }} />;
}

function Bubble({ role, content }) {
  const parts = formatText(content);
  const isUser = role === "user";
  return (
    <div style={{
      display: "flex",
      justifyContent: isUser ? "flex-end" : "flex-start",
      marginBottom: "6px",
    }}>
      <div style={{
        maxWidth: "72%",
        background: isUser ? "#1a1a1a" : "transparent",
        border: isUser ? "1px solid #2a2a2a" : "none",
        borderRadius: "14px",
        padding: isUser ? "10px 14px" : "4px 0",
        fontSize: "14px",
        lineHeight: "1.7",
        color: isUser ? "#e0e0e0" : "#c8c8c8",
        fontFamily: "'DM Sans', sans-serif",
      }}>
        {parts.map((p, i) =>
          p.type === "code" ? (
            <pre key={i} style={{
              background: "#111",
              border: "1px solid #222",
              borderRadius: "10px",
              padding: "14px 16px",
              overflowX: "auto",
              margin: "8px 0",
              fontSize: "12.5px",
              lineHeight: "1.65",
              color: "#a8d8a8",
              fontFamily: "'DM Mono', monospace",
            }}>
              <code>{p.content}</code>
            </pre>
          ) : (
            <InlineText key={i} text={p.content} />
          )
        )}
      </div>
    </div>
  );
}

function Typing() {
  return (
    <div style={{ padding: "4px 0", display: "flex", gap: "5px", alignItems: "center" }}>
      {[0, 1, 2].map(i => (
        <div key={i} style={{
          width: "6px", height: "6px",
          borderRadius: "50%",
          background: "#444",
          animation: "bounce 1.1s ease-in-out infinite",
          animationDelay: `${i * 0.18}s`,
        }} />
      ))}
    </div>
  );
}

const SUGGESTIONS = [
  "Объясни квантовые компьютеры просто",
  "Напиши сортировку пузырьком на Python",
  "Придумай название для IT-стартапа",
  "Как работает GPT?",
];

export default function App() {
  const [messages, setMessages] = useState([]);
  const [input, setInput] = useState("");
  const [loading, setLoading] = useState(false);
  const bottomRef = useRef(null);
  const textareaRef = useRef(null);

  useEffect(() => {
    bottomRef.current?.scrollIntoView({ behavior: "smooth" });
  }, [messages, loading]);

  function autoResize() {
    const el = textareaRef.current;
    if (!el) return;
    el.style.height = "auto";
    el.style.height = Math.min(el.scrollHeight, 140) + "px";
  }

  async function send(text) {
    const msg = text || input.trim();
    if (!msg || loading) return;
    setInput("");
    if (textareaRef.current) textareaRef.current.style.height = "auto";

    const newMessages = [...messages, { role: "user", content: msg }];
    setMessages(newMessages);
    setLoading(true);

    try {
      const res = await fetch("https://api.anthropic.com/v1/messages", {
        method: "POST",
        headers: {
          "Content-Type": "application/json",
          "anthropic-version": "2023-06-01",
          "anthropic-dangerous-direct-browser-access": "true",
        },
        body: JSON.stringify({
          model: MODEL,
          max_tokens: 1000,
          system: "Ты умный и лаконичный ассистент. Отвечай на языке пользователя. Будь полезным и точным.",
          messages: newMessages,
        }),
      });
      const data = await res.json();
      const reply = data.content?.[0]?.text || "Что-то пошло не так.";
      setMessages([...newMessages, { role: "assistant", content: reply }]);
    } catch {
      setMessages([...newMessages, { role: "assistant", content: "Ошибка соединения. Попробуй снова." }]);
    }
    setLoading(false);
  }

  const isEmpty = messages.length === 0;

  return (
    <>
      <style>{`
        @import url('https://fonts.googleapis.com/css2?family=DM+Sans:wght@300;400;500&family=DM+Mono:wght@400&display=swap');
        * { box-sizing: border-box; margin: 0; padding: 0; }
        body { background: #080808; }
        @keyframes bounce {
          0%, 60%, 100% { transform: translateY(0); opacity: 0.4; }
          30% { transform: translateY(-5px); opacity: 1; }
        }
        @keyframes fadeUp {
          from { opacity: 0; transform: translateY(8px); }
          to { opacity: 1; transform: translateY(0); }
        }
        textarea { outline: none; }
        textarea::-webkit-scrollbar { display: none; }
        code { font-family: 'DM Mono', monospace; background: #1a1a1a; padding: 1px 5px; border-radius: 5px; font-size: 12.5px; color: #a8d8a8; }
        b { color: #e0e0e0; font-weight: 500; }
        ::-webkit-scrollbar { width: 3px; }
        ::-webkit-scrollbar-track { background: transparent; }
        ::-webkit-scrollbar-thumb { background: #222; border-radius: 2px; }
      `}</style>

      <div style={{
        display: "flex",
        flexDirection: "column",
        height: "100vh",
        background: "#080808",
        fontFamily: "'DM Sans', sans-serif",
        color: "#e0e0e0",
      }}>

        {/* Header */}
        <div style={{
          padding: "18px 28px",
          borderBottom: "1px solid #141414",
          display: "flex",
          alignItems: "center",
          justifyContent: "space-between",
          flexShrink: 0,
        }}>
          <span style={{ fontSize: "15px", fontWeight: 500, letterSpacing: "-0.3px", color: "#fff" }}>
            нейрон
          </span>
          <span style={{ fontSize: "11px", color: "#333", letterSpacing: "0.05em" }}>
            claude sonnet
          </span>
        </div>

        {/* Chat */}
        <div style={{
          flex: 1,
          overflowY: "auto",
          padding: "24px 28px",
          display: "flex",
          flexDirection: "column",
        }}>
          {isEmpty ? (
            <div style={{
              flex: 1,
              display: "flex",
              flexDirection: "column",
              justifyContent: "center",
              alignItems: "flex-start",
              gap: "32px",
              animation: "fadeUp 0.5s ease",
            }}>
              <div>
                <div style={{ fontSize: "26px", fontWeight: 300, color: "#fff", letterSpacing: "-0.5px", marginBottom: "6px" }}>
                  Чем могу помочь?
                </div>
                <div style={{ fontSize: "13px", color: "#444", lineHeight: 1.6 }}>
                  Задай любой вопрос или выбери пример
                </div>
              </div>
              <div style={{ display: "flex", flexDirection: "column", gap: "8px", width: "100%", maxWidth: "420px" }}>
                {SUGGESTIONS.map((s, i) => (
                  <button key={i} onClick={() => send(s)} style={{
                    background: "transparent",
                    border: "1px solid #1e1e1e",
                    borderRadius: "10px",
                    padding: "10px 14px",
                    color: "#555",
                    fontSize: "13px",
                    fontFamily: "'DM Sans', sans-serif",
                    cursor: "pointer",
                    textAlign: "left",
                    transition: "border-color 0.15s, color 0.15s",
                  }}
                    onMouseEnter={e => { e.target.style.borderColor = "#333"; e.target.style.color = "#999"; }}
                    onMouseLeave={e => { e.target.style.borderColor = "#1e1e1e"; e.target.style.color = "#555"; }}
                  >
                    {s}
                  </button>
                ))}
              </div>
            </div>
          ) : (
            <div style={{ display: "flex", flexDirection: "column", gap: "4px" }}>
              {messages.map((m, i) => (
                <div key={i} style={{ animation: "fadeUp 0.25s ease" }}>
                  <Bubble role={m.role} content={m.content} />
                </div>
              ))}
              {loading && (
                <div style={{ animation: "fadeUp 0.2s ease" }}>
                  <Typing />
                </div>
              )}
            </div>
          )}
          <div ref={bottomRef} />
        </div>

        {/* Input */}
        <div style={{
          padding: "16px 28px 24px",
          flexShrink: 0,
          borderTop: "1px solid #141414",
        }}>
          <div style={{
            display: "flex",
            alignItems: "flex-end",
            gap: "10px",
            background: "#0f0f0f",
            border: "1px solid #1e1e1e",
            borderRadius: "14px",
            padding: "10px 10px 10px 16px",
          }}>
            <textarea
              ref={textareaRef}
              value={input}
              onChange={e => { setInput(e.target.value); autoResize(); }}
              onKeyDown={e => { if (e.key === "Enter" && !e.shiftKey) { e.preventDefault(); send(); } }}
              placeholder="Напишите сообщение..."
              rows={1}
              style={{
                flex: 1,
                background: "transparent",
                border: "none",
                color: "#e0e0e0",
                fontSize: "14px",
                fontFamily: "'DM Sans', sans-serif",
                lineHeight: "1.6",
                resize: "none",
                maxHeight: "140px",
                padding: "4px 0",
              }}
            />
            <button
              onClick={() => send()}
              disabled={!input.trim() || loading}
              style={{
                width: "34px", height: "34px",
                borderRadius: "9px",
                background: input.trim() && !loading ? "#e0e0e0" : "#1a1a1a",
                border: "none",
                cursor: input.trim() && !loading ? "pointer" : "not-allowed",
                display: "flex", alignItems: "center", justifyContent: "center",
                transition: "background 0.15s",
                flexShrink: 0,
              }}
            >
              <svg width="15" height="15" viewBox="0 0 24 24" fill="none"
                stroke={input.trim() && !loading ? "#080808" : "#333"}
                strokeWidth="2.2" strokeLinecap="round" strokeLinejoin="round">
                <line x1="22" y1="2" x2="11" y2="13" />
                <polygon points="22 2 15 22 11 13 2 9 22 2" />
              </svg>
            </button>
          </div>
          <div style={{ textAlign: "center", marginTop: "10px", fontSize: "11px", color: "#2a2a2a" }}>
            Enter — отправить · Shift+Enter — новая строка
          </div>
        </div>
      </div>
    </>
  );
}
