# Latex-Tetris-Game
\section*{IV. Cơ chế Gameplay cốt lõi}

\subsection*{1. Các loại khối}

\subsubsection*{1.1 Các Tetromino: I, O, T, S, Z, J, L.}

\noindent{Hình ảnh minh họa :}

\begin{center}
    \includegraphics[width=0.9\textwidth]{hinhanhvythe.jpg}
\end{center}
\renewcommand{\arraystretch}{2.0} % chỉnh hệ số giãn dòng
\begin{tabular}{|c|c|>{\centering\arraybackslash}p{8cm}|}
\hline
\textbf{Khối} & \textbf{Tên} & \textbf{Đặc điểm} \\
\hline
I & I-Tetrimino & Dài 4 ô thẳng hàng. Mạnh trong việc tạo Tetris (xóa 4 dòng). \\
\hline
O & O-Tetrimino & Hình vuông 2×2, không thay đổi hình dạng khi xoay. \\
\hline
T & T-Tetrimino & Dạng chữ T, linh hoạt, dễ xoay và xử lý nhiều tình huống. \\
\hline
J & J-Tetrimino & Hình chữ L ngược, tạo rãnh tốt. \\
\hline
L & L-Tetrimino & Hình chữ L, dùng để lấp góc hiệu quả. \\
\hline
S & S-Tetrimino & Dạng ziczac, thường khó xử lý nếu stack không phẳng. \\
\hline
Z & Z-Tetrimino & Tương tự S nhưng đối xứng ngược. \\
\hline
\end{tabular}

\vspace{1em}

\subsubsection*{1.2. Mỗi khối có hình dạng và cách xoay khác nhau.}
\begin{itemize}
    \item \textbf{Nguyên tắc xoay tổng  :}


Mỗi Tetromino có 4 trạng thái xoay tương ứng với các góc:
\[
0^\circ \rightarrow 90^\circ \rightarrow 180^\circ \rightarrow 270^\circ \rightarrow 0^\circ
\]

\item \textbf {Khi người chơi nhấn phím xoay, trò chơi thực hiện các bước:}

Khi bạn nhấn phím xoay, trò chơi sẽ lấy hình dạng và vị trí hiện tại của Tetrimino để chuẩn bị cho thao tác xoay. Đây là bước quan trọng để hệ thống biết khối nào đang được thao tác.

\vspace{0.03cm}
Tiếp theo, khối sẽ được xoay 90° theo chiều kim đồng hồ. Việc này thay đổi hướng và hình dạng của Tetrimino, giúp bạn linh hoạt sắp xếp các khối để lấp đầy các khoảng trống trên bảng chơi.

\vspace{0.03cm}
Ngay sau khi xoay, trò chơi sẽ kiểm tra xem khối có va chạm hay không. Khối không được vượt ra ngoài biên trái/phải, không rơi xuống sàn và không chồng lên các khối đã cố định. Việc kiểm tra này đảm bảo Tetrimino luôn nằm đúng vị trí và trò chơi diễn ra mượt mà.

\vspace{0.03cm}
Nếu xảy ra va chạm, cơ chế wall kick sẽ được kích hoạt. Trò chơi sẽ tự động đẩy khối sang trái hoặc phải 1–2 ô để tìm vị trí hợp lệ. Nhờ vậy, Tetrimino vẫn có thể xoay ngay cả khi gần tường hoặc sát các khối cố định, hạn chế tình trạng kẹt khối.

\vspace{0.03cm}
Trong trường hợp khối vẫn không thể đặt vào vị trí hợp lệ sau khi thử wall kick, thao tác xoay sẽ bị hủy và Tetrimino giữ nguyên trạng thái ban đầu. Điều này giúp trò chơi luôn ổn định và bạn không mất kiểm soát khối.

\vspace{0.03cm}
Nhờ cơ chế xoay kết hợp kiểm tra va chạm và wall kick, việc xoay Tetrimino trở nên mượt mà, dễ điều khiển và hạn chế tình trạng kẹt sát tường, mang lại trải nghiệm chơi Tetris trơn tru và thú vị hơn.

\vspace{0.03cm}
Nhờ cơ chế xoay + kiểm tra va chạm + wall kick, việc điều khiển Tetromino trở nên mượt mà và ổn định.
\end{itemize}
%---------------------------------------------------------------

\subsubsection*{2. Hệ thống điểm \& xếp hạng}

\begin{itemize}
    \item \textbf{Tính điểm}
\end{itemize}

Trong trò chơi, người chơi được thưởng điểm dựa trên số lượng hàng bị xóa trong một lượt.  
Xóa càng nhiều hàng thì điểm càng cao:

\begin{itemize}
    \item[\text{\large$\circ$}] 1 dòng xóa = \textbf{40 điểm}
    \item[\text{\large$\circ$}] 2 dòng xóa = \textbf{100 điểm}
    \item[\text{\large$\circ$}] 3 dòng xóa = \textbf{300 điểm}
    \item[\text{\large$\circ$}] 4 dòng xóa (Tetris) = \textbf{1200 điểm}
\end{itemize}
\begin{itemize}
    \item \textbf{Next Queue:} hiển thị trước khối tiếp theo, giúp người chơi chủ động lên chiến lược.  
\end{itemize}

\begin{itemize}
    \item \textbf{Tăng tốc độ rơi:}  sau mỗi 10 dòng được xóa, tốc độ rơi của khối tăng 10\%, khiến trò chơi thách thức dần theo thời gian.
\end{itemize}

% --------------------------------------------------------------

\subsubsection*{3. Khi nào trò chơi kết thúc?}

Trò chơi sẽ kết thúc khi không còn không gian để tạo vị trí xuất hiện cho khối mới.

\begin{itemize}
    \item Gạch chạm đỉnh → không thể sinh khối mới → \textbf{Game Over}
    \item Màn hình hiển thị: tổng điểm, số hàng đã xóa và level đạt được.
\end{itemize}

\section*{VI. Mẹo nâng cao \& những sai lầm cần tránh }

\begin{itemize}
    \item[-] {Hạn chế tạo khe trống, đặc biệt ở gần đáy}
\end{itemize}

Bạn nên tránh tạo ra các khe trống, đặc biệt là ở khu vực gần đáy.  
Những khoảng hở này thường rất khó lấp đầy và dễ khiến các khối phía trên bị dồn lên cao, làm tăng nguy cơ thua cuộc.

\begin{itemize}
    \item[-] {Tạo combo xóa nhiều hàng cùng lúc để ghi điểm cao}
\end{itemize}

Việc xóa nhiều hàng liên tiếp hoặc xóa nhiều hàng trong một lần sẽ giúp tăng điểm đáng kể.  
Vì vậy, người chơi nên xây dựng chiến thuật đặt khối hợp lý để tạo ra combo, tối ưu hóa số điểm qua từng lượt.

\begin{itemize}
     \item[-] {Ưu tiên sinh tồn khi tốc độ tăng, không quá mạo hiểm đặt khối}
\end{itemize}

Khi tốc độ rơi của các khối ngày càng nhanh, người chơi nên tập trung vào việc giữ playfield ổn định.  
Đừng quá mạo hiểm đặt các khối khó chỉ để kiếm thêm điểm, vì một sai sót nhỏ có thể khiến bàn chơi bị đầy rất nhanh.

\begin{itemize}
    \item[-] {Lưu ý: luôn sao lưu High Score nếu game có tính năng này}
\end{itemize}

Nếu trò chơi hỗ trợ tính năng lưu High Score, người chơi nên thường xuyên kiểm tra hoặc sao lưu để tránh mất dữ liệu thành tích.  
Điều này giúp bạn theo dõi tiến bộ và đặt ra mục tiêu rõ ràng hơn cho các lần chơi sau.
\end{document}
